---
title: Veri Sözleşmesi Bilinen Türler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 00ae32ff394b1ce2acb38fb237527e934934b935
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496015"
---
# <a name="data-contract-known-types"></a>Veri Sözleşmesi Bilinen Türler
<xref:System.Runtime.Serialization.KnownTypeAttribute> Sınıfı, öncelikli göz önünde bulundurarak seri durumdan çıkarma sırasında için dahil edilecek türleri belirtmenize olanak verir. Çalışan bir örnek için bkz: [bilinen türleri](../../../../docs/framework/wcf/samples/known-types.md) örnek.  
  
 Normalde, parametreler ve dönüş değerleri bir istemci ve hizmet arasında geçirirken, her iki uç noktalar tüm aktarılacak olan verilerin veri sözleşmeleri paylaşır. Ancak, aşağıdaki koşullarda durumda değil:  
  
-   Gönderilen veri sözleşmesi beklenen veri sözleşmeden türetilir. Daha fazla bilgi için devralma hakkındaki bölüme bakın [veri sözleşmesi eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). Bu durumda, aktarılan verilerin alıcı bitiş noktası tarafından beklendiği gibi sözleşme aynı veri yok.  
  
-   Aktarılacak türü bilgileri için bir sınıf, yapı veya numaralandırma aksine bir arabirimdir. Bu nedenle, bu önceden uygulayan arabirimi gerçekte gönderilir ve bu nedenle, alıcı endpoint iletilen veriler veri sözleşmesi önceden belirleyemiyor tür bilinmesi olamaz.  
  
-   Aktarılacak bildirilen türü bilgi <xref:System.Object>. Her tür devraldığı çünkü <xref:System.Object>ve bunu önceden hangi tür gerçekte gönderilen bilinmesi olamaz, alıcı uç noktası önceden iletilen veriler veri sözleşmesi belirleyemiyor. Bu bir ilk öğe özel durumdur: her veri sözleşmesi için oluşturulan bir boş veri sözleşmesi varsayılan türetilen <xref:System.Object>.  
  
-   Dahil bazı türleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri, önceki üç kategoriden birinde üyelerin sahiptir. Örneğin, <xref:System.Collections.Hashtable> kullanan <xref:System.Object> karma tablosunda gerçek nesneleri depolamak için. Bu tür serileştirme, alma tarafı önceden bu üyeler için veri sözleşmesi belirleyemiyor.  
  
## <a name="the-knowntypeattribute-class"></a>KnownTypeAttribute sınıfı  
 Veri alma bitiş noktasına ulaştığında, WCF çalışma zamanı verileri bir ortak dil çalışma zamanı (CLR) türünün bir örneği seri durumdan dener. İlk veri belirlemek için gelen ileti sözleşme iletinin içeriğini uygun olması inceleyerek çıkarma için örneği türü seçilir. Seri durumdan çıkarma altyapısı sonra ileti içeriği ile uyumlu bir veri sözleşmesi uygulayan bir CLR türü bulmaya çalışır. Bu işlem sırasında seri durumdan çıkarma altyapısı izin veren adayı türleri kümesi "bilinen türler." seri kaldırıcı'nın kümesi verilir  
  
 Türü hakkında bilmeniz seri durumdan çıkarma altyapısı izin vermek için bir yoldur kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute>. Öznitelik, yalnızca tüm veri sözleşme türleri için ayrı veri üyelerine uygulanamaz. Öznitelik uygulanan bir *dış türü* bir sınıf veya bir yapı olabilir. En temel kullanımını öznitelik uygulama türü "bilinen bir tür olarak." belirtir Bu bilinen türleri dış türünde bir nesne her bir parçası olarak bilinen türü neden olur veya üyeleri başvurulan herhangi bir nesne seri durumdan çıkarılmakta olan. Birden fazla <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği aynı türüne uygulanabilir.  
  
## <a name="known-types-and-primitives"></a>Bilinen türleri ve temelleri  
 İlkel türler olarak belirli türleri temel olarak kabul edilir (örneğin, <xref:System.DateTime> ve <xref:System.Xml.XmlElement>) her zaman "bilinen" ve hiçbir zaman bu mekanizma eklenmesi gerekir. Ancak, ilkel türlerin dizileri açıkça eklenmesi gerekir. Çoğu koleksiyonları diziler için eşdeğer olarak değerlendiriliyor. (Olmayan genel koleksiyonlar için dizileri eşdeğer değerlendirilir <xref:System.Object>). Kullanarak bir örnek temelleri, basit diziler ve ilkel koleksiyonlar, örnek 4 bakın.  
  
> [!NOTE]
>  Başka ilkel türler aksine <xref:System.DateTimeOffset> yapısı değil varsayılan olarak, bilinen bir türe şekilde el ile bilinen türleri listesine eklenmelidir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örneklerde gösterildiği <xref:System.Runtime.Serialization.KnownTypeAttribute> sınıfı kullanımda.  
  
#### <a name="example-1"></a>Örnek 1  
 Üç sınıflarıyla bir devralma ilişkisi vardır.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Aşağıdaki `CompanyLogo` sınıfı hale getirilebilir, varsa kaldırılamaz ancak `ShapeOfLogo` üye olarak ayarlanmış çok ya da bir `CircleType` veya `TriangleType` nesne seri durumdan çıkarma altyapısı herhangi bir veri sözleşmesi adları türleriyle tanımadığından " Daire"veya"Üçgen."  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Yazmak için doğru bir şekilde `CompanyLogo` türü aşağıdaki kodda gösterilir.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Her dış türü `CompanyLogo2` olan bildiği seri durumdan çıkarma altyapısı seri durumdan çıkarılmakta `CircleType` ve `TriangleType` ve bu nedenle, eşleşen türleri için "Daire" ve "Üçgen" veri sözleşmeleri bulamıyor.  
  
#### <a name="example-2"></a>Örnek 2  
 Aşağıdaki örnekte, olsa da her ikisini de `CustomerTypeA` ve `CustomerTypeB` sahip `Customer` veri sözleşmesi, örneği `CustomerTypeB` ne zaman oluşturulur bir `PurchaseOrder` , çünkü seri durumdan olan yalnızca `CustomerTypeB` bilinen seri durumdan çıkarma altyapısı.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnekte, bir <xref:System.Collections.Hashtable> içeriğinin depolar dahili olarak <xref:System.Object>. Başarıyla bir karma tablosu seri durumdan çıkarılacak seri durumdan çıkarma altyapısı var. oluşabilecek olası türleri kümesini bilmeniz gerekir. Bu durumda, önceden yalnızca biliyoruz `Book` ve `Magazine` nesneleri depolanır `Catalog`, bu kullanılarak eklenen <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Örnek 4  
 Aşağıdaki örnekte, bir sayı ve bir işlem sayısına gerçekleştirmek için bir veri sözleşmesi depolar. `Numbers` Veri üyesi dizisi, bir tamsayı olabilir veya bir <xref:System.Collections.Generic.List%601> tamsayılar içerir.  
  
> [!CAUTION]
>  Bu yalnızca istemci tarafında çalışmayacak SVCUTIL. EXE WCF proxy oluşturmak için kullanılır. SVCUTIL. EXE herhangi bilinen türleri dahil olmak üzere hizmetinden meta verilerini alır. Bu bilgiler olmadan bir istemci türleri seri durumdan mümkün olmaz.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Uygulama kodu budur.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Bilinen türler, devralma ve arabirimleri  
 Bilinen bir türe olduğunda belirli türünü kullanarak ilişkili `KnownTypeAttribute` özniteliği, bilinen türü de türetilmiş türler bu türdeki tüm ile ilişkili. Örneğin, aşağıdaki kodu bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` Sınıfı gerektirmez `KnownTypeAttribute` kullanmak için öznitelik `Square` ve `Circle` içinde `AdditionalShape` , çünkü alan temel sınıfı (`Drawing`) zaten uygulanan bu özniteliklere sahiptir.  
  
 Bilinen türler yalnızca sınıfları ve yapıları, arabirimler değil ile ilişkili olabilir.  
  
## <a name="known-types-using-open-generic-methods"></a>Açık genel yöntemler kullanarak bilinen türler  
 Genel bir tür bilinen bir türe eklemek gerekli olabilir. Ancak, açık genel tür parametre olarak gönderilemez. `KnownTypeAttribute` özniteliği.  
  
 Alternatif bir mekanizma kullanarak bu sorun çözülebilir: bilinen türleri koleksiyona eklemek için türlerinin bir listesini döndüren bir yöntem yazma. Yöntemin adını sonra bir dize bağımsız değişkeni olarak belirtilen `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliği.  
  
 Yöntemi hangi türünde bulunmalıdır `KnownTypeAttribute` özniteliği uygulanır, statik olmalıdır, herhangi bir parametre kabul etmeniz gerekir ve atanabilir bir nesne döndürmelidir <xref:System.Collections.IEnumerable> , <xref:System.Type>.  
  
 Birleştiremez `KnownTypeAttribute` bir yöntem adı özniteliğiyle ve `KnownTypeAttribute` gerçek türlerinde aynı türde olan öznitelikler. Ayrıca, birden fazla uygulanamıyor `KnownTypeAttribute` bir yöntem adı aynı türe sahip.  
  
 Aşağıdaki sınıf bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` Alan genel bir sınıf örneklerini içerir `ColorDrawing` ve genel bir sınıf `BlackAndWhiteDrawing`, her ikisi de bir genel sınıfından `Drawing`. Normalde, hem bilinen türleri eklenmesi gerekir, ancak şu öznitelikler için geçerli sözdizimi değil.  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 Bu nedenle, bu tür döndürmek için bir yöntem oluşturulması gerekir. Bu tür yazmak için doğru bir şekilde daha sonra aşağıdaki kodda gösterilir.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Bilinen türler eklemek için başka bir yolu  
 Ayrıca, bilinen türleri bir yapılandırma dosyası eklenebilir. Bu, uygun seri durumdan çıkarma üçüncü taraf kullanarak yazdığınızda kitaplıkları ile Windows Communication Foundation (WCF) gibi bilinen türleri gerektiren türü kontrol etmez durumunda faydalı olur.  
  
 Aşağıdaki yapılandırma dosyası, bilinen bir türe bir yapılandırma dosyası belirtmek gösterilmiştir.  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 Adlı bir veri sözleşmesi türü yukarıdaki yapılandırmada dosya `MyCompany.Library.Shape` sağlamak için bildirilen `MyCompany.Library.Circle` bilinen türü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [Bilinen Türler](../../../../docs/framework/wcf/samples/known-types.md)  
 [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)
