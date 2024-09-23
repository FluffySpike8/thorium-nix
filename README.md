# Thorium Browser for Nix

Nix flake for Thorium Browser

# Usage

```nix
# flake.nix

{
  inputs.thorium-browser.url = "git+https://github.com/FluffySpike8/thorium-nix";
  # ...

  outputs = {nixpkgs, ...} @ inputs: {
    nixosConfigurations.HOSTNAME = nixpkgs.lib.nixosSystem {
      specialArgs = { inherit inputs; }; # this is the important part
      modules = [
        ./configuration.nix
      ];
    };
  }
}

# configuration.nix

{inputs, pkgs, ...}: {
  # ...
  environment.systemPackages = [
    inputs.thorium-browser.defaultPackage.${system}
  ];
  # ...
}
```

# Acknowledgments

This project is based on the work of [Tomkoid](https://codeberg.org/tomkoid/thorium-browser-nix).
