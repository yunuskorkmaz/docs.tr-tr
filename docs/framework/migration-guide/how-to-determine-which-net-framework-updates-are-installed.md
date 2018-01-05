---
title: "Nasıl yapılır: hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri yüklü olduğunu belirleme"
description: "Hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri bir bilgisayarda yüklü olduğunu belirleme hakkında bilgi edinin."
ms.date: 11/27/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad61ce44c24f48b51c32eb554e8d37932d119af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Nasıl yapılır: hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri yüklü olduğunu belirleme

Düzeltmeler bir bilgisayarda yüklü olan ve bu makalede hangi .NET Framework güvenlik güncelleştirmeleri çıkışı bulmak nasıl gösterir.

> [!NOTE]
> Bu makalede gösterilen tüm teknikler yönetici ayrıcalıklarına sahip bir hesabı gerektirir.

## <a name="to-find-installed-updates-using-the-registry"></a>Bulmak için kayıt defterini kullanarak güncelleştirmeleri yüklü

Yüklü olan güvenlik güncelleştirmeleri ve düzeltmeleri her bir bilgisayarda yüklü .NET Framework sürümü için Windows Kayıt Defteri'nde listelenir. Kayıt Defteri Düzenleyicisi'ni kullanabilirsiniz (*regedit.exe*) bu bilgileri görüntülemek için program.

1. Programını açın **regedit.exe**. Windows 8 ve sonraki sürümlerinde sağ **Başlat** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")seçeneğini belirleyip **çalıştırmak**. İçinde **açık** kutusuna **regedit** seçip **Tamam**.

2. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Yüklü güncelleştirmeler için geçerlidir .NET Framework sürümünü tanımlamak alt anahtarları altında listelenir. Her güncelleştirme bir Bilgi Bankası (KB) numarasına göre tanımlanır.

Kayıt Defteri Düzenleyicisi'nde, .NET Framework sürümleri ve her sürüm için yüklü güncelleştirmeler farklı alt anahtarlarında saklanır. Yüklü sürüm numaralarını algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Bulunacak kodu kayıt defterinde sorgulayarak yüklü güncelleştirmeleri

Aşağıdaki örnek, .NET Framework güvenlik güncelleştirmeleri ve bir bilgisayarda yüklü olan düzeltmelerin programlı olarak belirler:

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Bulmak için PowerShell kayıt defterinde sorgulayarak yüklü güncelleştirmeleri

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

[Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)  
[Sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md)
