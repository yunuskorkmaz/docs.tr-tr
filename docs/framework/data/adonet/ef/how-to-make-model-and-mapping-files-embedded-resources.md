---
title: "Nasıl yapılır: yapma modeli ve eşleme dosyaları katıştırılmış kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98fb3ada369279a34ed08110644aabcbbe72a501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Nasıl yapılır: yapma modeli ve eşleme dosyaları katıştırılmış kaynakları
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Modeli ve eşleme dosyaları uygulamanın gömülü kaynaklar dağıtmanıza olanak tanır. Varlık bağlantısı aynı uygulama etki alanında katıştırılmış modeli ve eşleme dosyaları içeren derlemenin yüklü olması gerekir. Daha fazla bilgi için bkz: [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Varsayılan olarak, [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları katıştırmak modeli ve eşleme dosyaları. Model ve eşleme dosyaları el ile tanımladığınızda, dosyaları ile birlikte gömülü kaynaklar olarak dağıtıldığından emin olmak için bu yordamı kullanın bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.  
  
> [!NOTE]
>  Katıştırılmış kaynakları korumak için model ve eşleme dosyaları değiştirdiğinde bu yordamı yineleyin gerekir.  
  
### <a name="to-embed-model-and-mapping-files"></a>Model ve eşleme dosyaları eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kavramsal (.csdl) dosyasını seçin.  
  
2.  İçinde **özellikleri** kümesi bölmesi, **yapı eylemi** için **katıştırılmış kaynak**.  
  
3.  Depolama (.ssdl) dosyası ve eşleme (.msl) dosyası için 1 ve 2. adımları yineleyin.  
  
4.  İçinde **Çözüm Gezgini**, App.config dosyasına çift tıklayın ve ardından değiştirme `Metadata` parametresinde `connectionString` özniteliği aşağıdaki biçimlerden birini temel alarak:  
  
    -   `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=``res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Daha fazla bilgi için bkz: [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki bağlantı dizesi başvuran katıştırılmış modeli ve eşleme dosyaları için [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Bu bağlantı dizesi projenin App.config dosyasında depolanır.  
  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme ve eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Nasıl yapılır: bağlantı dizesi tanımlayın](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [Nasıl yapılır: bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
