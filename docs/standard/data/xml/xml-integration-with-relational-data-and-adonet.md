---
title: İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbc381395720b6b63a8cdfb44c55808d4608e77f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831988"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi
**XmlDataDocument** , türetilmiş bir sınıfı **XmlDocument**ve XML verileri içerir. Avantajı **XmlDataDocument** ilişkisel ve hiyerarşik veriler arasında bir köprü sağlar. Bu bir **XmlDocument** için bağlanabilir bir **veri kümesi** ve hem sınıflarını iki sınıflarında bulunan verilere yapılan değişiklikleri eşitleyebilirsiniz. Bir **XmlDocument** bağlanan bir **veri kümesi** ilişkisel veriler ile tümleştirmek XML verir ve verilerinizin ya da XML olarak veya bir biçimde temsil gerekmez. Her ikisini de yapabilirsiniz ve tek bir veri temsilini için kısıtlı olabilir değil.  
  
 Verilerin iki görünümlerde kullanılabilir olduğu avantajları şunlardır:  
  
-   Bir XML belgesi yapılandırılmış kısmı bir veri kümesine eşlenmesi verimli bir şekilde depolanan, dizine ve Aranan.  
  
-   Verimli bir şekilde dönüştürmeleri, doğrulama ve gezinti gösterim depolanır XML verilerinde bir imleç modeli aracılığıyla yapılabilir. Bazen, bunu daha verimli bir şekilde XML içinde depolanıyorsa daha ilişkisel yapıları karşı yapılabilir bir **XmlDocument** modeli.  
  
-   **Veri kümesi** XML'nin bir kısmı depolayabilirsiniz. Diğer bir deyişle, kullanabileceğiniz **XPath** veya **XslTransform** için depolamak için bir **veri kümesi** yalnızca bu öğeler ve öznitelikler ilgi. Büyük veriler üzerinde yayma değişikliklerle daha küçük, filtrelenmiş veri alt kümesini için değişiklik yapılamaz buradan **XmlDataDocument**.  
  
 İçine yüklenen veriler üzerinde dönüşüm çalıştırabilirsiniz **veri kümesi** SQL Server'dan. .NET Framework sınıfları stili yönetilen WinForm bağlamak için başka bir seçenektir ve WebForm denetimleri bir **veri kümesi** XML giriş akışından doldurulmuş.  
  
 Destek yanı sıra **XslTransform**, bir **XmlDataDocument** ilişkisel veri sunan **XPath** sorgular ve doğrulama.  Temel olarak, tüm XML Hizmetleri ilişkisel veriler üzerinde kullanılabilir ve denetim bağlama codegen ve benzeri gibi ilişkisel tesis XML yapılandırılmış bir projeksiyon üzerinde XML uygunluk ödün vermeden kullanılabilir.  
  
 Çünkü **XmlDataDocument** devralınan bir **XmlDocument**, W3C yerli uygulaması sağlar Olgu, **XmlDataDocument** ilişkili olduğu ve depolar, içinde verilerin bir alt kümesini bir **veri kümesi** değil erişimi kısıtlamak veya kullanımını alter bir **XmlDocument** herhangi bir şekilde. Kodu kullanmak için yazılan bir **XmlDocument** works değiştirilmeden karşı bir **XmlDataDocument**. **Veri kümesi** tablolar, sütunlar, ilişkiler ve kısıtlamalar tanımlayarak aynı verilerin ilişkisel görünümünü sağlar ve tek başına, bellek içi kullanıcı veri deposudur.  
  
 XML verileri ile olduğunu farklı ilişkilendirmeleri aşağıda gösterilmiştir **veri kümesi** ve **XmlDataDocument**: 
  
 ![XML veri kümesi ile farklı ilişkileri gösteren diyagram.](./media/xml-integration-with-relational-data-and-adonet/xml-integration-relational-data-adodotnet.gif)  
  
 XML verileri doğrudan içine yüklenemez çizimin gösterdiği bir **veri kümesi**, ilişkisel bir biçimde XML doğrudan düzenlenmesini sağlar. Veya, XML, türetilmiş bir sınıf olan DOM yüklenebilir **XmlDataDocument**, daha sonra yüklenen ve eşitlenmiş **veri kümesi**. Çünkü **veri kümesi** ve **XmlDataDocument** tek bir küme üzerinde eşitlenir verilerinin diğer deposunda bir depo verilerde yapılan değişiklikler yansıtılır.  
  
 **XmlDataDocument** tüm düzenleme ve gezinti özellikleri devralır **XmlDocument**. Bazı durumlarda kullanırken **XmlDataDocument** ve eşitlenmiş özelliklerini devralınan bir **veri kümesi**, doğrudan XML yüklenirken değerinden daha uygun bir seçenektir **verikümesi**. Aşağıdaki tabloda, hangi yöntemin yüklemek için kullanılacağını seçerken göz önünde bulundurulması öğeleri gösterilmektedir **veri kümesi**.  
  
|Bir veri kümesine doğrudan XML yükleme zamanı|Bir veri kümesiyle bir XmlDataDocument eşitleme zamanı|  
|----------------------------------------------|-----------------------------------------------------------|  
|Veri sorguları **veri kümesi** kullanarak SQL XPath daha kolaydır.|XPath sorguları, verileri üzerinde gereklidir **veri kümesi**.|  
|Öğenin kaynak XML sıralama korunması kritik değildir.|Öğenin kaynak XML sıralama korunması kritik öneme sahiptir.|  
|Öğeleri ve biçimlendirme arasında yer alan kaynak XML korunması gerekmez.|Boşluk ve ' % s'kaynağındaki XML Biçimlendirme korunması kritik.|  
  
 Yükleme ve XML doğrudan tanesi yazma bir **veri kümesi** ihtiyaçlarınızı adresleri bkz [XML'den DataSet yükleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML verileri olarak DataSet yazma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Yükleniyor, **veri kümesi** gelen bir **XmlDataDocument** ihtiyaçlarınızı adresleri bkz [bir XML belgesi bir Datasetwith eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
