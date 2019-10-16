---
title: 'Nasıl yapılır: hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin yüklendiğini belirleme'
description: Bir bilgisayara hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin yüklendiğini belirlemeyi öğrenin.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c69d4bb370087dddafbfed41cbfb1fef229677c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318965"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Nasıl yapılır: hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin yüklendiğini belirleme

Bu makalede, bir bilgisayara hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklendiğini nasıl bulacağınız açıklanmaktadır.

> [!NOTE]
> Bu makalede gösterilen tüm teknikler, yönetici ayrıcalıklarına sahip bir hesap gerektirir.

## <a name="to-find-installed-updates-using-the-registry"></a>Kayıt defterini kullanarak yüklü güncelleştirmeleri bulmak için

Bir bilgisayarda yüklü .NET Framework her sürümü için yüklü güvenlik güncelleştirmeleri ve düzeltmeleri Windows kayıt defterinde listelenmiştir. Bu bilgileri görüntülemek için kayıt defteri Düzenleyicisi (*Regedit. exe*) programını kullanabilirsiniz.

1. **Regedit. exe**programını açın. Windows 8 ve sonraki sürümlerde, ![Windows anahtar logosunun ekran görüntüsünü] **Başlat** ' a sağ tıklayın. (./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")ve **Çalıştır**' ı seçin. **Aç** kutusunda, **Regedit** yazın ve **Tamam**' ı seçin.

2. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Yüklü güncelleştirmeler, için uygulandıkları .NET Framework sürümünü tanımlayan alt anahtarlar altında listelenir. Her güncelleştirme bir Bilgi Bankası (KB) numarasıyla tanımlanır.

Kayıt defteri düzenleyicisinde, her sürüm için .NET Framework sürümleri ve yüklü güncelleştirmeler farklı alt anahtarlarda saklanır. Yüklü sürüm numaralarını algılama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Kod içinde kayıt defterini sorgulayarak yüklü güncelleştirmeleri bulmak için

Aşağıdaki örnek, bir bilgisayarda yüklü olan .NET Framework güvenlik güncelleştirmelerini ve düzeltmeleri programlı bir şekilde belirler:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Örnek aşağıdakine benzer bir çıktı üretir:

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>PowerShell 'de kayıt defterini sorgulayarak yüklü güncelleştirmeleri bulmak için

Aşağıdaki örnek, PowerShell kullanarak bir bilgisayarda yüklü olan .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin nasıl belirleneceğini göstermektedir:

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

Örnek aşağıdakine benzer bir çıktı üretir:

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md)
- [Geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md)
- [Sürümler ve bağımlılıklar](versions-and-dependencies.md)
