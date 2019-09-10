---
title: 'Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 371f8f0317295ee39d543b5637afb93102036b62
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854596"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma
Entity Framework, bir uygulamanın katıştırılmış kaynakları olarak model ve eşleme dosyalarını dağıtmanıza olanak sağlar. Katıştırılmış model ve eşleme dosyaları olan derlemenin, varlık bağlantısıyla aynı uygulama etki alanında yüklü olması gerekir. Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md). Varsayılan olarak, Varlık Veri Modeli araçları modeli ve eşleme dosyalarını gömer. Model ve eşleme dosyalarını el ile tanımladığınızda, dosyaların bir Entity Framework uygulamayla birlikte gömülü kaynaklar olarak dağıtıldığından emin olmak için bu yordamı kullanın.  
  
> [!NOTE]
> Katıştırılmış kaynakları korumak için, model ve eşleme dosyaları her değiştirildiğinde bu yordamı yinelemeniz gerekir.  
  
### <a name="to-embed-model-and-mapping-files"></a>Model ve eşleme dosyalarını eklemek için  
  
1. **Çözüm Gezgini**, kavramsal (. csdl) dosyasını seçin.  
  
2. **Özellikler** bölmesinde, **derleme eylemini** **katıştırılmış kaynak**olarak ayarlayın.  
  
3. Depolama (. ssdl) dosyası ve eşleme (. MSL) dosyası için 1 ve 2. adımları tekrarlayın.  
  
4. **Çözüm Gezgini**, App. config dosyasına çift tıklayın ve ardından `Metadata` `connectionString` özniteliğinde parametresini aşağıdaki biçimlerden birine göre değiştirin:  
  
    - `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=``res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki bağlantı dizesi, [AdventureWorks Sales modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)için gömülü modele ve eşleme dosyalarına başvurur. Bu bağlantı dizesi projenin App. config dosyasında depolanır.  

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleme ve Eşleme](modeling-and-mapping.md)
- [Nasıl yapılır: Bağlantı dizesini tanımlama](how-to-define-the-connection-string.md)
- [Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma](how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
