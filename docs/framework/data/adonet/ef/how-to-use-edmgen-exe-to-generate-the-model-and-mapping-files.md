---
title: "Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları oluşturmak için kullanın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ebff53126b808f679855b43fd8e1d2461b516e66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları oluşturmak için kullanın
Bu konuda EDM Oluşturucu (EdmGen.exe) aracı Okul veritabanını temel alan aşağıdaki dosyaları oluşturmak için nasıl kullanılacağı gösterilmektedir:  
  
-   Kavramsal model (.csdl dosyası).  
  
-   Depolama modeli (.ssdl dosyası).  
  
-   Kavramsal ve depolama modelleri (.msl dosyası) arasında eşleme.  
  
-   Visual Basic veya C# kodunda nesne katmanı.  
  
-   Dosyaları görüntüleyin.  
  
 EdmGen.exe aracı /mode:FullGeneration yukarıda listelenen dosyaları oluşturmak için kullanır. EdmGen.exe komutları hakkında daha fazla bilgi için bkz: [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Model ve eşleme dosyaları oluşturmak için EdmGen.exe kullanırsanız hala yapılandırmanız gereken, [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] kullanmak için proje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: bir Entity Framework projesi el ile yapılandırmanız](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  EdmGen.exe tarafından oluşturulan kavramsal model veritabanındaki tüm nesneleri içerir. Yalnızca belirli nesneleri içeren bir kavramsal model oluşturmak istiyorsanız, varlık veri modeli Sihirbazı'nı kullanın. Daha fazla bilgi için bkz: [nasıl yapılır: Varlık veri modeli Sihirbazı'nı](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe kullanarak bir Visual Basic proje Okul model oluşturmak için  
  
1.  Okul veritabanı oluşturun. Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Okul model EdmGen.exe kullanarak bir C# projesi oluşturmak için  
  
1.  Okul veritabanı oluşturun. Daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme ve Eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Nasıl yapılır: bir Entity Framework projesi el ile yapılandırma](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Nasıl yapılır: sorgu performansını artırmak için görünümlerini önceden oluşturmak](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
