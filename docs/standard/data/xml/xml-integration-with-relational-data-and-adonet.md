---
title: İlişkisel veri ve ADO.NET XML tümleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e9bdb9b88d51e5435609bbab8bbe21a985505a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>İlişkisel veri ve ADO.NET XML tümleştirme
**XmlDataDocument** sınıftır türetilen bir sınıftan **XmlDocument**ve XML verileri içerir. Avantajı **XmlDataDocument** ilişkisel ve hiyerarşik veri arasında bir köprü sağlamasıdır. Bu bir **XmlDocument** için bağlanabilir bir **DataSet** ve her iki sınıfları iki sınıflarında bulunan verilere yapılan değişiklikleri eşitleyebilirsiniz. Bir **XmlDocument** için bağlı bir **DataSet** ilişkisel veri ile tümleştirmek XML sağlar ve her iki XML olarak veya ilişkisel bir biçimde gösterilen verilerinizi gerekmez. Her ikisini birden yapın ve verileri tek bir gösterimini kısıtlanacak değil.  
  
 Verileri iki görünümlerinde bulundurmak avantajları şunlardır:  
  
-   Bir XML belgesi yapılandırılmış kısmı bir veri kümesine eşlenmesi verimli bir şekilde depolanan, dizine ve aranır.  
  
-   Verimli bir şekilde dönüşümleri, doğrulama ve gezinti imleç modeli aracılığıyla gösterim depolanan XML verileri yapılabilir. Bazen, daha verimli bir şekilde XML içinde depolanıyorsa daha ilişkisel yapıları karşı yapılabilir bir **XmlDocument** modeli.  
  
-   **DataSet** XML bir kısmı depolayabilirsiniz. Diğer bir deyişle, kullanabileceğiniz **XPath** veya **çok** için depolamak için bir **DataSet** yalnızca bu öğeleri ve özniteliklerinin ilgi. Daha büyük verilerde yayılıyor değişikliklerle daha küçük, filtrelenmiş veri alt kümesini için değişiklikler yapılabilir buradan **XmlDataDocument**.  
  
 İçine yüklenen veriler üzerinde bir dönüşüm çalıştırabilirsiniz **DataSet** SQL Server'dan. .NET Framework sınıfları stili yönetilen WinForm bağlamak için başka bir seçenektir ve WebForm denetimleri için bir **DataSet** XML giriş akışından doldurulmuş.  
  
 Destekleyen yanı sıra **çok**, bir **XmlDataDocument** ilişkisel veri sunan **XPath** sorgular ve doğrulama.  Temel olarak, tüm XML Hizmetleri ilişkisel veri kullanılabilir ve denetim bağlama, codegen ve vb. gibi ilişkisel tesis yapılandırılmış bir XML yansıtma XML uygunluğunu ödün vermeden kullanılabilir.  
  
 Çünkü **XmlDataDocument** devralınan bir **XmlDocument**, W3C DOM uygulaması sağlar Olgu, **XmlDataDocument** ilişkili olduğu ve bir veri alt kümesini kendi içinde depolar bir **DataSet** kısıtlamak veya değil olarak kullanılmasını alter bir **XmlDocument** herhangi bir şekilde. Kullanmak için yazılan kod bir **XmlDocument** works değiştirilmemiş karşı bir **XmlDataDocument**. **DataSet** tablolar, sütunlar, ilişkileri ve kısıtlamaları tanımlayarak aynı verileri ilişkisel görünümünü sağlar ve bir tek başına, bellek içi kullanıcı veri deposudur.  
  
 XML verileri ile sahip farklı ilişkilendirmeleri aşağıda gösterilmiştir **DataSet** ve **XmlDataDocument**.  
  
 ![XML veri kümesi](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 XML verileri doğrudan yüklenebilir gösterimde bir **DataSet**, ilişkisel bir biçimde XML doğrudan düzenlenmesini sağlar. Veya XML türetilmiş olan DOM sınıfına yüklenebilir **XmlDataDocument**, daha sonra yüklenen ve eşitlenmiş **DataSet**. Çünkü **DataSet** ve **XmlDataDocument** tek bir küme üzerinde eşitlenir verilerinin bir depoya verilerde yapılan değişiklikleri bir depolama alanına yansıtılır.  
  
 **XmlDataDocument** tüm düzenleme ve gezinti özellikleri devralır **XmlDocument**. Zamanlar kullanırken **XmlDataDocument** ve eşitlenmiş özelliklerini devralınan bir **DataSet**, doğrudan XML yükleme değerinden daha uygun bir seçenektir **DataSet**. Aşağıdaki tabloda yüklemek için kullanılacak yöntemi seçme göz önünde bulundurulması öğelerine gösterilmektedir **DataSet**.  
  
|Doğrudan bir veri kümesini XML yükleme zamanı|XmlDataDocument bir veri kümesi ile eşitleme zamanı|  
|----------------------------------------------|-----------------------------------------------------------|  
|Veri sorguları **DataSet** XPath'den SQL kullanarak daha kolaydır.|XPath sorguları gerekli verileri üzerinden **DataSet**.|  
|XML kaynağında sıralama öğesinin korunması kritik değildir.|XML kaynağında sıralama öğesinin korunması önemlidir.|  
|Öğeleri ve biçimlendirme arası boşluk XML kaynağında korunması gerekmez.|Boşluk ve XML kaynağındaki biçimlendirme koruma kritik.|  
  
 Yükleme ve XML yazma doğrudan ve işyeri dışında bir **DataSet** gereksinimlerinizi adresleri bkz [bir veri kümesini XML dosyası şuradan yükleniyor](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [bir veri kümesini XML verileri olarak yazma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Yükleme, **DataSet** gelen bir **XmlDataDocument** gereksinimlerinizi adresleri bkz [Datasetwith bir XML belgesi eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet içinde XML kullanma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
