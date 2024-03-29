# BrickServerInterface
<br />
<p align="center">
<a href="https://github.com/BricksVR-Modding/BricksVR-Modding-Guide">
    <img src="https://avatars.githubusercontent.com/u/94014912?s=200&v=4" alt="Logo" width="80" height="80">
  </a>
  <h3 align="center"><u>BricksVR Modding</u></h3>

  <p align="center">
    A simple repo that explains the basics, anyone can upload their mods here!
    <br />
    <br />
    <br />
    <a href="https://github.com/zakmasood/BricksVRModding">Github</a>
    ·
    <a href="https://github.com/zakmasood/BricksVRModding/issues/new">Report An Issue</a>
    ·
    <a href="https://github.com/zakmasood/BricksVRModding/issues/new">Request A Feature</a>
  </p>
</p>

  [![Contributors][contributors-shield]][contributors-url]
  [![Forks][forks-shield]][forks-url]
  [![Stargazers][stars-shield]][stars-url]
  [![Issues][issues-shield]][issues-url]
  [![MIT License][license-shield]][license-url]
## About

The BrickServerInterface is a in-game script that manages the room, this includes the brick count, changing nicknames, and getting room info.

## Examples

```cs
    var exampleVariable = BrickServerInterface;
    exampleVariable.setNickname("Josh.");
```
```cs
    var rt = Realtime
    var exampleVariable = BrickServerInterface;
    exampleVariable.setLocked(true, rt);
```

## Why do the functions not exist?
In your code editor you may try:
```cs
    BrickServerInterface.setNickname("Bob's Milk.");
```
However when you try to do this it will not work because you are using the class instead of the instance. To fix this problem you will need to get the component, to do this you can use the GetInstance method.
```cs
    BrickServerInterface.GetInstance().setNickname("The revenge of Bob.")
```

## Methods & Examples

`SendBrick(NormcoreRPC.Brick brick, Realtime realtime)`

This is not how you place in-game bricks. To place in-game bricks you must use the BrickSwapper script. This updates the brick count.
```cs
    var realtime = GameObject.Find("MetaObjects/Realtime").GetComponent<Realtime>();

    var brick = new NormcoreRPC.Brick { uuid = "test", matId = 93, color = 23, type = "2x2", pos = new Vector3(0, 0, 0), rot = new Quaternion(0f, 0f, 0f, 0f), usingNewColor = false, headClientId = -1, usingHeadStuff = true };

    BrickServerInterface.GetInstance().sendBrick(brick, realtime);
```

`RemoveBrick(string uuid, Realtime realtime)`

Tells server to remove a brick from the brick count by uuid.
```cs
    var realtime = GameObject.Find("MetaObjects/Realtime").GetComponent<Realtime>();

    BrickServerInterface.GetInstance().RemoveBrick("test", realtime);
```

`SetLocked(bool locked, Realtime realtime)`

Locks the room, however you must be the room owner for this to function properly.
```cs
    var realtime = GameObject.Find("MetaObjects/Realtime").GetComponent<Realtime>();

    BrickServerInterface.GetInstance().SetLocked(true, realtime);
```

`SetNickname(nickname)`

Changes *your* nickname.
```cs
    BrickServerInterface.GetInstance().SetNickname("Bob,\nWhat have these monsters done to you?");
```

## Source Code:
[BrickServerInterface.cs](https://github.com/d12/bricksvr-game/blob/main/Assets/Scripts/BrickServerInterface.cs)

[contributors-shield]: https://img.shields.io/github/contributors/zakmasood/BricksVRModding.svg?style=for-the-badge
[contributors-url]: https://github.com/zakmasood/BricksVRModding/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/zakmasood/BricksVRModding.svg?style=for-the-badge
[forks-url]: https://github.com/https://github.com/zakmasood/BricksVRModding/network/members
[stars-shield]: https://img.shields.io/github/stars/zakmasood/BricksVRModding.svg?style=for-the-badge
[stars-url]: https://github.com/zakmasood/BricksVRModdingstargazers
[issues-shield]: https://img.shields.io/github/issues/zakmasood/BricksVRModding.svg?style=for-the-badge
[issues-url]: https://github.com/zakmasood/BricksVRModding
[license-shield]: https://img.shields.io/github/license/zakmasood/BricksVRModding.svg?style=for-the-badge
[license-url]: https://github.com/zakmasood/BricksVRModding/blob/main/LICENSE
