---
title: 'Nasıl yapılır: Model ve eşleme dosyalarını gömülü kaynak'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 0fd7e4fe751fd05a8b48f3dee79d374f669917fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660352"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Nasıl yapılır: Model ve eşleme dosyalarını gömülü kaynak
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Model ve eşleme dosyalarını gömülü kaynaklar bir uygulama dağıtmanıza olanak sağlar. Varlık bağlantı aynı uygulama etki alanında derleme ekli model ve eşleme dosyalarını ile yüklü olması gerekir. Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Varsayılan olarak, [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları, model ve eşleme dosyalarını ekleyin. Model ve eşleme dosyalarını el ile tanımladığınızda, dosyaları ile birlikte gömülü kaynak olarak dağıtıldığından emin olmak için bu yordamı kullanın bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.  
  
> [!NOTE]
>  Katıştırılmış kaynakları korumak için model ve eşleme dosyalarını değiştirdiğinde bu yordamı yineleyin gerekir.  
  
### <a name="to-embed-model-and-mapping-files"></a>Model ve eşleme dosyalarını eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kavramsal (.csdl) dosyasını seçin.  
  
2.  İçinde **özellikleri** bölmesinde, **derleme eylemi** için **gömülü kaynak**.  
  
3.  Depolama (.ssdl) dosyası ve eşleme (.msl) dosyası için 1 ve 2 numaralı adımları tekrarlayın.  
  
4.  İçinde **Çözüm Gezgini**, App.config dosyasına çift tıklayın ve ardından değişiklik `Metadata` parametresinde `connectionString` özniteliği aşağıdaki biçimlerden birini temel alan:  
  
    -   `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=``res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Örnek  
 Ekli model ve eşleme dosyaları için aşağıdaki bağlantı dizesi başvuran [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Bu bağlantı dizesi, projenin App.config dosyasında depolanır.  
  
  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Modelleme ve Eşleme](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Nasıl yapılır: Bağlantı dizesi tanımlama](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET varlık veri modeli araçları](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
