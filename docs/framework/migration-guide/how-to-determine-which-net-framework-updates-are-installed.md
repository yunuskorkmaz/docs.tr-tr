---
title: "Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a>Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme
Her bir bilgisayarda yüklü .NET Framework sürümü için yüklü güncelleştirmeler Windows Kayıt Defteri'nde listelenir. Bu bilgileri görüntülemek için Kayıt Defteri Düzenleyicisi'ni (regedit.exe) kullanabilirsiniz.  
  
 Kayıt Defteri Düzenleyicisi'nde, .NET Framework sürümleri ve her sürüm için yüklü güncelleştirmeler farklı alt anahtarlarında saklanır. Yüklü sürüm numaralarını algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirlemek, .NET Framework sürümlerinin yüklendiğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). .NET Framework yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../docs/framework/install/guide-for-developers.md).  
  
### <a name="to-find-installed-updates"></a>Yüklü güncelleştirmeleri bulmak için  
  
1.  Programını açın **regedit.exe**. Windows 8 ve üzeri başlangıç ekranını açmak ve bir ad yazın. Önceki Windows sürümlerinde üzerinde **Başlat** menüsünde seçin **çalıştırmak** , daha sonra **açık** kutusuna **regedit.exe**.  
  
     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.  
  
2.  Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates  
  
     Yüklü güncelleştirmeler için geçerlidir .NET Framework sürümünü tanımlamak alt anahtarları altında listelenir. Her güncelleştirme bir Bilgi Bankası (KB) numarasına göre tanımlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir bilgisayarda yüklü olan .NET Framework güncelleştirmeleri programlı olarak belirler. Bu örneği çalıştırmak için yönetici kimlik bilgileriniz olması gerekir.  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 Örnekte aşağıdakine benzer bir çıktı oluşturulur:  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[.NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md)   
[Sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md)
