---
title: Yüklü .NET Framework güvenlik güncelleştirmelerini ve düzeltmelerini görün
description: Bilgisayarda hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklü olduğunu nasıl belirleyeceğimiz öğrenin.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181276"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklendiği nasıl belirlenir?

Bu makalede, bir bilgisayarda hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin yüklü olduğunu nasıl bulacağınızı gösterir.

> [!NOTE]
> Bu makalede gösterilen tüm teknikler, yönetim ayrıcalıkları olan bir hesap gerektirir.

## <a name="use-registry-editor"></a>Kayıt Defteri Düzenleyicisi'ni kullanma

Bir bilgisayara yüklenen .NET Framework'ün her sürümü için yüklenen güvenlik güncelleştirmeleri ve düzeltmeleri Windows kayıt defterinde listelenir. Bu bilgileri görüntülemek için Kayıt Defteri Düzenleyicisi *(regedit.exe)* programını kullanabilirsiniz.

1. Programı **açın regedit.exe**. Windows 8 ve sonraki sürümlerde, ![Windows tuşu logosunun](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")Ekran **Run**Görüntüsünü **Başlat'ı** sağ tıklatın. **Aç** kutusuna **regedit'i** girin ve **Tamam'ı**seçin.

2. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\Güncellemeler**

     Yüklenen güncelleştirmeler, uyguladıkları .NET Framework sürümünü tanımlayan alt anahtarların altında listelenir. Her güncelleştirme bir Bilgi Bankası (KB) numarası yla tanımlanır.

In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys. Yüklü sürüm numaralarını algılama hakkında bilgi için [bkz: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleyin.](how-to-determine-which-versions-are-installed.md)

## <a name="query-the-registry-using-code"></a>Kodu kullanarak kayıt defterini sorgula

Aşağıdaki örnek, bilgisayarda yüklenen .NET Framework güvenlik güncelleştirmelerini ve düzeltmeleri programlı olarak belirler:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Örnek, aşağıdakine benzer bir çıktı üretir:

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

## <a name="use-powershell-to-query-the-registry"></a>Kayıt defterini sorgulamak için PowerShell'i kullanma

Aşağıdaki örnek, PowerShell kullanarak bir bilgisayara yüklenen .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin nasıl belirlendiğini gösterir:

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

Örnek, aşağıdakine benzer bir çıktı üretir:

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

- [Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](how-to-determine-which-versions-are-installed.md)
- [Geliştiriciler için .NET Framework'u yükleyin](../install/guide-for-developers.md)
- [Sürümler ve bağımlılıklar](versions-and-dependencies.md)
