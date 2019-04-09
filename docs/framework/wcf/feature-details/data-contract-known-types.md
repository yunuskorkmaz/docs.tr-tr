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
ms.openlocfilehash: bedf35544454a32ff13856a072779cd70723e989
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129629"
---
# <a name="data-contract-known-types"></a>Veri Sözleşmesi Bilinen Türler
<xref:System.Runtime.Serialization.KnownTypeAttribute> Sınıfı, öncelikli seri durumundan çıkarma sırasında göz önünde bulundurmanız için dahil edilmesi gereken türleri belirtmenize olanak verir. Çalışan bir örnek için bkz. [bilinen türleri](../../../../docs/framework/wcf/samples/known-types.md) örnek.  
  
 Normalde, parametreler ve dönüş değerleri bir istemci ve hizmet arasında geçirirken, her iki bitiş tüm aktarılacak olan verilerin veri sözleşmeleri paylaşır. Ancak, bu durum aşağıdaki durumlarda geçerli değildir:  
  
-   Gönderilen veri anlaşması beklenen veri sözleşme üzerinden türetilir. Bölüm içinde devralma hakkında daha fazla bilgi için bkz. [veri anlaşması eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). Bu durumda, aktarılan veri alan uç noktası tarafından beklenen şekilde sözleşme aynı veri yok.  
  
-   İletilecek bilgiler için bildirilen tür bir sınıf, yapı ya da numaralandırma aksine bir arabirimdir. Bu nedenle, bunu önceden uyguladığı arabirim gerçekten gönderilir ve bu nedenle, alıcı uç nokta aktarılan veriler için veri anlaşması önceden belirleyemiyor tür bilinmesi olamaz.  
  
-   İletilecek bilgiler için bildirilen türü <xref:System.Object>. Her tür öğesinden devralındığından <xref:System.Object>ve bunu önceden hangi tür gerçekten gönderilen bilinmesi olamaz, alan uç noktası önceden aktarılan veriler için veri anlaşması belirlenemiyor. Bu, ilk öğenin bir özel durumdur: Varsayılan olarak oluşturulan bir boş veri anlaşması her veri anlaşması türetildiği <xref:System.Object>.  
  
-   Dahil bazı türleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri, önceki üç kategoriden birinde yer üyelerin sahiptir. Örneğin, <xref:System.Collections.Hashtable> kullanan <xref:System.Object> karma tablosundan gerçek nesneleri depolamak için. Bu türler seri hale getirme, alma tarafı önceden bu üyeler için veri anlaşması belirlenemiyor.  
  
## <a name="the-knowntypeattribute-class"></a>KnownTypeAttribute sınıfı  
 Veri alma bir bitiş noktasına ulaştığında, bir ortak dil çalışma zamanı (CLR) türünün bir örneğine verileri seri durumdan WCF çalıştırma zamanı çalışır. İlk verileri belirlemek için gelen ileti anlaşması iletinin içeriğini uygun olması inceleyerek seri durumundan çıkarma için örneği türü seçilir. Seri durumundan çıkarma altyapısı ardından ileti içeriği ile uyumlu bir veri anlaşması uygulayan bir CLR türü bulmaya çalışır. Bu işlem sırasında seri durumundan çıkarma altyapısı sağlayan aday türleri "bilinen türleri." seri kaldırıcı'nın kümesi olarak adlandırılır  
  
 Bir tür hakkında bilmeniz seri durumundan çıkarma altyapısının yollarından biri açıklanmıştır kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute>. Öznitelik, yalnızca tüm veri anlaşması türleri için tek tek veri üyeleri için uygulanamaz. Öznitelik uygulandığı bir *dış türün* bir sınıf veya yapı olabilir. En temel kullanımını özniteliği uygulama türü "bilinen bir tür olarak." belirtir Bu neden olan bilinen türleri dış türün bir nesnenin her bir parçası olarak bilinen türü veya üyelerini başvurulan herhangi bir nesne seri durumdan çıkarılmakta olan. Birden fazla <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği aynı türe uygulanabilir.  
  
## <a name="known-types-and-primitives"></a>Bilinen türler ve temelleri  
 İlkel türler olarak belirli türlerini temel olarak kabul edilir (örneğin, <xref:System.DateTime> ve <xref:System.Xml.XmlElement>) her zaman "bilinen" ve hiçbir zaman bu mekanizma aracılığıyla eklenmesi gerekir. Ancak, ilkel türlerin dizileri açıkça eklenmesi gerekir. Çoğu koleksiyonları diziler için eşdeğer olarak kabul edilir. (Genel olmayan koleksiyon dizileri için eşdeğer olarak değerlendirilir <xref:System.Object>). Kullanma örneği için temelleri, basit diziler ve temel koleksiyonları örnek 4 bakın.  
  
> [!NOTE]
>  Diğer ilkel türler, aksine <xref:System.DateTimeOffset> yapısı bir bilinen tür değil varsayılan olarak, böylece el ile bilinen türler listesine eklenmelidir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örneklerde gösterildiği <xref:System.Runtime.Serialization.KnownTypeAttribute> sınıfı kullanın.  
  
#### <a name="example-1"></a>Örnek 1  
 Devralma ilişkisi ile üç sınıfı vardır.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Aşağıdaki `CompanyLogo` sınıfı serileştirilmiş, ancak, seri durumdan çıkarılamıyor `ShapeOfLogo` üye ayarlanmış olarak bir `CircleType` veya `TriangleType` nesne seri durumundan çıkarma altyapısı herhangi bir veri sözleşmesi adları türleriyle tanımadığından " Daire"veya"Üçgen."  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Yazma için doğru şekilde `CompanyLogo` türü, aşağıdaki kodda gösterilmiştir.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Her dış türün `CompanyLogo2` olan bildiği seri durumundan çıkarma altyapısı seri durumdan çıkarılmakta `CircleType` ve `TriangleType` ve bu nedenle, eşleşen türleri için "Daire" ve "Üçgen" veri sözleşmeleri bulabilirsiniz.  
  
#### <a name="example-2"></a>Örnek 2  
 Aşağıdaki örnekte, olsa bile her ikisi de `CustomerTypeA` ve `CustomerTypeB` sahip `Customer` veri anlaşması, örneği `CustomerTypeB` herhangi bir zamanda oluşturulmuş bir `PurchaseOrder` , çünkü seri durumda yalnızca `CustomerTypeB` bilinen Seri durumundan çıkarma altyapısı.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnekte, bir <xref:System.Collections.Hashtable> içeriğini depolar dahili olarak <xref:System.Object>. Bir karma tablo başarılı bir şekilde seri durumdan çıkarılacak seri durumundan çıkarma altyapısı var. oluşabilecek olası türleri bilmeniz gerekir. Bu durumda, yalnızca bilgimiz `Book` ve `Magazine` nesnelerinin depolandığı `Catalog`, bu kullanılarak eklenen <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Örnek 4  
 Aşağıdaki örnekte, bir sayı ve bir işlem sayısına gerçekleştirmek için bir veri anlaşması depolar. `Numbers` Veri üyesi, bir tamsayı dizisi, olabilir veya bir <xref:System.Collections.Generic.List%601> tamsayılar içeren.  
  
> [!CAUTION]
>  Bu yalnızca istemci tarafında ise çalışır SVCUTIL. EXE, WCF proxy oluşturmak için kullanılır. SVCUTIL. EXE herhangi bir bilinen türleri dahil olmak üzere hizmet meta verilerini alır. Bu bilgiler olmadan, bir istemci türleri seri durumdan çıkarılacak mümkün olmayacaktır.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Uygulama kodu budur.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Bilinen türler, devralma ve arabirimler  
 Bilinen bir türde olduğunda kullanarak bir türdeki ilişkili `KnownTypeAttribute` özniteliği, bilinen türü de tüm türetilmiş türleri türü ile ilişkili. Örneğin, aşağıdaki koda bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` Sınıfı gerektirmez `KnownTypeAttribute` kullanılacak özniteliği `Square` ve `Circle` içinde `AdditionalShape` çünkü alan taban sınıf (`Drawing`) zaten uygulanan bu özniteliklere sahip.  
  
 Bilinen türler yalnızca sınıflar ve yapılar, arabirimler değil ile ilişkili olabilir.  
  
## <a name="known-types-using-open-generic-methods"></a>Açık genel yöntemler kullanarak bilinen türler  
 Genel bir tür bilinen bir tür eklemek gerekli olabilir. Ancak, bir açık genel tür parametresi olarak geçirilemez `KnownTypeAttribute` özniteliği.  
  
 Bu sorun, alternatif bir mekanizma kullanarak çözülebilir: Bilinen türlerin koleksiyonuna eklemek için türlerinin bir listesini döndüren bir yöntem yazmaktır. Yöntemin adını ardından bir dize bağımsız değişkeni olarak belirtilen `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliği.  
  
 Yöntem türü üzerinde bulunmalıdır `KnownTypeAttribute` özniteliği uygulanır, statik olmalıdır, hiçbir parametre kabul etmeniz gerekir ve atanabilir bir nesne döndürmelidir <xref:System.Collections.IEnumerable> , <xref:System.Type>.  
  
 Birleştirmeniz mümkün olmayacaktır `KnownTypeAttribute` özniteliği bir metot adı ile ve `KnownTypeAttribute` özniteliklerle aynı türünde gerçek türler. Ayrıca, birden fazla uygulanamıyor `KnownTypeAttribute` bir yöntem adı aynı türe sahip.  
  
 Aşağıdaki sınıf konusuna bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` Alan içeren bir genel sınıfın örnekleri `ColorDrawing` ve genel bir sınıf `BlackAndWhiteDrawing`, ikisi için de genel bir sınıftan devralınan `Drawing`. Normalde, her ikisi de bilinen türlere eklenen gerekir, ancak aşağıdaki öznitelikleri sözdizimi geçerli değil.  
  
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
  
 Bu nedenle, bu tür döndürmek için bir yöntem oluşturulması gerekir. Bu tür, yazma için doğru şekilde, daha sonra aşağıdaki kodda gösterilir.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Bilinen türler eklemek için ek yol  
 Ayrıca, bilinen türleri bir yapılandırma dosyası eklenebilir. Bilinen türler için uygun seri durumundan çıkarma gibi üçüncü taraf kullanarak yazdığınızda kitaplıkları ile Windows Communication Foundation (WCF) gerektiren türü kontrol edebilirim istediğinizde yararlıdır.  
  
 Aşağıdaki yapılandırma dosyası, bir yapılandırma dosyasında bir bilinen türü belirtmek gösterilmektedir.  
  
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
  
 Önceki yapılandırma dosyası adlı bir veri anlaşması türü `MyCompany.Library.Shape` için bildirilen `MyCompany.Library.Circle` bilinen türü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Bilinen Türler](../../../../docs/framework/wcf/samples/known-types.md)
- [Veri Sözleşmesi Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)
