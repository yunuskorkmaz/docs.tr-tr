---
title: 'Nasıl yapılır: Hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri yüklü olduğunu belirleme'
description: Hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri bir bilgisayarda yüklü olduğunu belirleme hakkında bilgi edinin.
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
ms.openlocfilehash: e11b2588471e95b4e47fd0efaf41757430b9bb39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604193"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Nasıl yapılır: Hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri yüklü olduğunu belirleme

Bu makalede, hangi .NET Framework güvenlik güncelleştirmeleri kullanıma bulma işlemini göstermektedir ve düzeltmeler bir bilgisayara yüklenir.

> [!NOTE]
> Bu makalede gösterilen teknikleri, yönetici ayrıcalıklarına sahip bir hesabı gerektirir.

## <a name="to-find-installed-updates-using-the-registry"></a>Bulmak için kayıt defterini kullanarak güncelleştirmeleri yüklü

Yüklü güvenlik güncelleştirmeleri ve düzeltmeleri her bir bilgisayarda yüklü .NET Framework sürümü için Windows kayıt defterinde listelenir. Kayıt Defteri Düzenleyicisi'ni kullanabilirsiniz (*regedit.exe*) bu bilgileri görüntülemek için program.

1. Programı açtığınızda **regedit.exe**. Windows 8 ve sonraki sürümlerinde, sağ **Başlat** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), ardından **çalıştırma**. İçinde **açık** kutusuna **regedit** seçip **Tamam**.

2. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Yüklü güncelleştirmeleri uygulandıkları .NET Framework sürümünü tanımlayan alt altında listelenir. Her güncelleştirme bir Bilgi Bankası (KB) numarasıyla tanımlanır.

Kayıt Defteri Düzenleyicisi'nde, .NET Framework sürümleri ve her sürümü için yüklü güncelleştirmeleri farklı alt anahtarlarında saklanır. Yüklü sürüm numaraları algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Bulmak için kod içinde kayıt defterini sorgulayarak yüklü güncelleştirmeleri

Aşağıdaki örnek, bir bilgisayarda yüklü olan düzeltmelerin ve .NET Framework güvenlik güncelleştirmeleri programlı olarak belirler:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Örnekte aşağıdakine benzer bir çıktı oluşturulur:

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Bulmak için PowerShell içinde kayıt defterini sorgulayarak yüklü güncelleştirmeleri

Aşağıdaki örnek .NET Framework güvenlik güncelleştirmeleri ve PowerShell kullanarak bir bilgisayarda yüklü olan düzeltmelerin belirlemek nasıl gösterir:

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

Örnekte aşağıdakine benzer bir çıktı oluşturulur:

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

- [Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)
- [Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)
- [Sürümler ve bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)
