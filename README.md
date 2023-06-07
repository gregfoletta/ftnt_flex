# NAME

ftnt\_flex - register new FortiFlex licenses

# VERSION

version .1

# SYNOPSIS

    # List current configurations
    ./ftnt_flex --list-configs
    - Authentication Success
    - Configurations:
      - FGT_UTM_8CPU_5VDOM (FortiGate-VM)
      - FWB_2CPU_ADV (FortiWeb-VM)
      ...


    # Create a new entitlement
    ./ftnt_flex --new-entitlement FGT_UTM_8CPU_5VDOM
    - Authentication Success
    - New entitlements created successfully
      - Serial: FZVMELTM23000338, Token: 379CDFxxxxxxxxxxxxxx

# OPTIONS

- -u|--username _user_ - the FortiCloud API username
- -p|--password _pass_ - the FortiCloud API password
- -l|--list-configs - List current configurations and exit.
- -n|--new-entitlement &lt;config\_name> - Create a new entitlement based on the configuration specified.
- --count - Number of entitlements to create. If not specified, 1 x entitlement will be created.
- -h|--help - print usage information

# DESCRIPTION

# REQUIREMENTS

You'll need the following modules, preferably installed using the more modern [cpanminus](https://metacpan.org/pod/App::cpanminus):

    sh$ cpanm Mojo::UserAgent IO::Socket::SSL

or the old CPAN client:

    sh$ cpan Mojo::UserAgent IO::Socket::SSL

# AUTHENTICATION

The script uses version 3 of the registration API. This uses OAuth tokens generated from IAM API username/passwords. You can create IAM users [here](https://support.fortinet.com/iam/#/api-user).

Once you have your credentials, the script will search for them in three places:

- In ~/.ftnt/ftnt\_cloud\_api formatted as &lt;username>:&lt;password>
    - Lines beginning with '#' are skipped
- In the environment variabes `FORTICLOUD_API_USER` and `FORTICLOUD_API_PASSWORD`
- In the command line arguments `-u|--username` and `-p|--password`.

If the credentials are available in multiple places, local dotfile beats environment variable beats commandline.

Note that the password has an exclaimation mark in it, so be sure to enclose in single quotes if you're using the environment variable or command line methods.
