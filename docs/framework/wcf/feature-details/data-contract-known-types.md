---
title: Veri Sözleşmesi Bilinen Türler
description: Veri anlaşması modelinin, WCF 'de seri durumundan çıkarma sırasında dahil edilecek türleri belirtmek için KnownTypeAttribute sınıfını nasıl kullandığını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 52b0caaaac976893dcf5ef5c228ccc4f53bdbe9e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247487"
---
# <a name="data-contract-known-types"></a>Veri Sözleşmesi Bilinen Türler
<xref:System.Runtime.Serialization.KnownTypeAttribute>Sınıfı, serisini kaldırma sırasında dikkate alınması gereken türleri önceden belirtmenize olanak tanır. Çalışan bir örnek için, [bilinen türler](../samples/known-types.md) örneğine bakın.  
  
 Normalde, parametreleri geçirirken ve bir istemci ile bir hizmet arasında değer döndürmelerinde, her iki uç nokta de iletilmek üzere verilerin tüm veri sözleşmelerini paylaşır. Ancak, aşağıdaki durumlarda bu durum böyle değildir:  
  
- Gönderilen veri sözleşmesi, beklenen veri sözleşmesinden türetilir. Daha fazla bilgi için, [veri sözleşmesindeki](data-contract-equivalence.md)devralma hakkında bölümüne bakın. Bu durumda, iletilen veriler, alıcı uç noktası tarafından beklenen veri sözleşmesine sahip değildir.  
  
- İletilecek bilgiler için, bir sınıf, yapı veya numaralandırmanın aksine, bir arabirim olduğu bildirilmiştir. Bu nedenle, arabirimi uygulayan türün gerçekten gönderildiği ve bu nedenle alıcı uç noktasının iletilen veriler için veri sözleşmesinin ön planda belirleyemediği bilinmez.  
  
- İletilecek bilgiler için belirtilen tür <xref:System.Object> . Her tür öğesinden devralındığından <xref:System.Object> ve bu türün gerçekten gönderildiği bilinmediği için, alıcı uç noktası aktarılan verilerin veri sözleşmesinin ön planda saptanamıyor. Bu, ilk öğenin özel bir durumdur: her veri sözleşmesi, için oluşturulan boş bir veri sözleşmesinin varsayılan değerinden türetilir <xref:System.Object> .  
  
- .NET Framework türlerini içeren bazı türlerin önceki üç kategoriden birinde olan üyeleri vardır. Örneğin, <xref:System.Collections.Hashtable> <xref:System.Object> karma tablodaki gerçek nesneleri depolamak için kullanır. Bu türler serileştirilirken, alıcı taraf bu üyeler için veri sözleşmesinin ön kısmına göre saptanamaz.  
  
## <a name="the-knowntypeattribute-class"></a>KnownTypeAttribute sınıfı  
 Veriler alma uç noktasına ulaştığında, WCF çalışma zamanı verileri ortak dil çalışma zamanı (CLR) türünün bir örneğine serisini kaldırma girişiminde bulunur. Seri durumdan çıkarma için örneği oluşturulan tür, önce iletinin içeriğinin uyumlu olduğu veri sözleşmesinin belirlenmesi için gelen iletiyi inceleyerek seçilir. Seri kaldırma altyapısı daha sonra ileti içeriğiyle uyumlu bir veri sözleşmesi uygulayan bir CLR türü bulmaya çalışır. Seri durumdan çıkarma altyapısının bu işlem sırasında izin verdiği aday türleri kümesi, seri hale getirici 'nin "bilinen türler" kümesi olarak adlandırılır.  
  
 Seri durumdan çıkarma altyapısının bir tür hakkında bilgi almasına imkan sağlamanın bir yolu, ' nı kullanmaktır <xref:System.Runtime.Serialization.KnownTypeAttribute> . Öznitelik, tek tek veri üyelerine yalnızca tüm veri anlaşması türlerine uygulanamaz. Özniteliği, bir sınıf veya yapı olabilecek bir *dış türe* uygulanır. En temel kullanımındaki özniteliği uygulamak, bir türü "bilinen tür" olarak belirtir. Bu, dış türdeki bir nesne veya üyeleri aracılığıyla başvurulan herhangi bir nesne seri durumdan çıkarıldığı zaman bilinen türün bilinen türler kümesinin bir parçası olmasına neden olur. <xref:System.Runtime.Serialization.KnownTypeAttribute>Aynı türde birden fazla öznitelik uygulanabilir.  
  
## <a name="known-types-and-primitives"></a>Bilinen türler ve temel elemanlar  
 İlkel türler ve temel öğeler (örneğin, ve) olarak değerlendirilen belirli türler <xref:System.DateTime> <xref:System.Xml.XmlElement> her zaman "biliniyor" ve bu mekanizmaya hiç eklenmemek zorunda değildir. Ancak, temel türlerin dizileri açıkça eklenmelidir. Çoğu koleksiyon dizilere eşit kabul edilir. (Genel olmayan koleksiyonlar diziler için eşdeğer olarak kabul edilir <xref:System.Object> ). Temel elemanlar, ilkel diziler ve basit koleksiyonlar kullanmanın bir örneği için bkz. örnek 4.  
  
> [!NOTE]
> Diğer temel türlerin aksine, <xref:System.DateTimeOffset> Yapı varsayılan olarak bilinen bir tür değildir, bu nedenle bilinen türler listesine el ile eklenmelidir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örneklerde <xref:System.Runtime.Serialization.KnownTypeAttribute> kullanılan sınıf gösterilmektedir.  
  
#### <a name="example-1"></a>Örnek 1  
 Devralma ilişkisine sahip üç sınıf vardır.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Aşağıdaki `CompanyLogo` sınıf seri hale getirilebilir, ancak `ShapeOfLogo` üye bir ya da bir nesne olarak ayarlandıysa seri durumdan çıkarılamaz, `CircleType` `TriangleType` çünkü serisini kaldırma altyapısı veri sözleşme adları "Circle" veya "Triangle" olan herhangi bir türü tanımaz.  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 Türü yazmanın doğru yolu `CompanyLogo` aşağıdaki kodda gösterilmiştir.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Dış tür `CompanyLogo2` seri durumdan çıkarılabildiğinde, seri durumdan çıkarma motoru `CircleType` ve ile ilgili olarak, `TriangleType` "daire" ve "üçgen" veri sözleşmeleri için eşleşen türleri bulabilir.  
  
#### <a name="example-2"></a>Örnek 2  
 Aşağıdaki örnekte, her ikisi de `CustomerTypeA` ve veri sözleşmesine sahip olsa bile, her `CustomerTypeB` `Customer` `CustomerTypeB` bir seri hale geldiğinde bir örneği oluşturulur `PurchaseOrder` , çünkü yalnızca seri durumdan `CustomerTypeB` çıkarma altyapısı tarafından bilinir.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnekte, bir, <xref:System.Collections.Hashtable> içeriğini dahili olarak depolar <xref:System.Object> . Bir karma tablonun serisini başarıyla kaldırmak için, seri durumdan çıkarma altyapısının, burada oluşabilecek olası türler kümesini bilmeleri gerekir. Bu durumda, yalnızca `Book` ve `Magazine` nesnelerinin üzerinde depolandıkları için, bu, `Catalog` öznitelik kullanılarak eklenmeleri durumunda olduğunu biliyoruz <xref:System.Runtime.Serialization.KnownTypeAttribute> .  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Örnek 4  
 Aşağıdaki örnekte, bir veri sözleşmesi numarayı ve numara üzerinde gerçekleştirilecek bir işlemi depolar. `Numbers`Veri üyesi tamsayı, tamsayılar dizisi veya tamsayılar içeren bir dize olabilir <xref:System.Collections.Generic.List%601> .  
  
> [!CAUTION]
> Bu, yalnızca bir WCF proxy oluşturmak için SVCUTIL.EXE kullanılıyorsa istemci tarafında çalışır. SVCUTIL.EXE bilinen türler dahil olmak üzere hizmetten meta verileri alır. Bu bilgiler olmadan, istemci türlerin serisini kaldıramıyor.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Bu uygulama kodudur.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Bilinen türler, devralma ve arabirimler  
 Bilinen bir tür özniteliği kullanılarak belirli bir türle ilişkilendirildiğinde `KnownTypeAttribute` , bilinen tür aynı zamanda bu türün türetilmiş tüm türleri ile ilişkilendirilir. Örneğin, aşağıdaki koda bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` `KnownTypeAttribute` `Square` `Circle` `AdditionalShape` Temel sınıf ( `Drawing` ) zaten bu özniteliklerin uygulanmış olması nedeniyle, sınıfı, ' ın ve alan içinde özniteliğini gerektirmez.  
  
 Bilinen türler, arabirimler değil yalnızca sınıflar ve yapılar ile ilişkilendirilebilir.  
  
## <a name="known-types-using-open-generic-methods"></a>Açık genel yöntemler kullanan bilinen türler  
 Bilinen bir tür olarak genel bir tür eklemek gerekebilir. Ancak açık genel tür özniteliğe parametre olarak geçirilemez `KnownTypeAttribute` .  
  
 Bu sorun, alternatif bir mekanizma kullanılarak çözülebilir: bilinen türler koleksiyonuna eklemek üzere türlerin bir listesini döndüren bir yöntem yazın. Yöntemin adı, daha sonra `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliğe dize bağımsız değişkeni olarak belirtilir.  
  
 Yöntemin, özniteliğin uygulandığı türde olması gerekir `KnownTypeAttribute` , statik olması gerekir, parametre içermemelidir ve ' nin atanabileceği bir nesne döndürmesi gerekir <xref:System.Collections.IEnumerable> <xref:System.Type> .  
  
 `KnownTypeAttribute`Özniteliği, `KnownTypeAttribute` aynı türde gerçek türler içeren bir yöntem adı ve özniteliklerle birleştiremezsiniz. Ayrıca, `KnownTypeAttribute` aynı türde bir yöntem adına sahip birden fazla tane uygulayamazsınız.  
  
 Aşağıdaki sınıfa bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing`Alan, her ikisi de genel bir sınıftan devraldığı bir genel sınıfın `ColorDrawing` ve genel sınıfın örneklerini içerir `BlackAndWhiteDrawing` `Drawing` . Normalde, her ikisi de bilinen türlere eklenmelidir, ancak öznitelikler için geçerli sözdizimi şu değildir.  
  
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
  
 Bu nedenle, bu türleri döndürmek için bir yöntem oluşturulmalıdır. Bu türü yazmanın doğru yolu aşağıdaki kodda gösterilmiştir.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Bilinen türleri eklemenin ek yolları  
 Ayrıca, bilinen türler bir yapılandırma dosyası aracılığıyla eklenebilir. Bu, Windows Communication Foundation (WCF) ile üçüncü taraf tür kitaplıkları kullanırken olduğu gibi, doğru seri durumundan çıkarma için bilinen türler gerektiren türü denetlemediğinde yararlıdır.  
  
 Aşağıdaki yapılandırma dosyasında, bir yapılandırma dosyasında bilinen bir türün nasıl belirtilmesi gösterilmektedir.  
  
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
  
 Yukarıdaki yapılandırma dosyasında, çağrılan bir veri anlaşması türü `MyCompany.Library.Shape` bilinen bir tür olacak şekilde bildirilmiştir `MyCompany.Library.Circle` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Bilinen Türler](../samples/known-types.md)
- [Veri Sözleşmesi Eşitliği](data-contract-equivalence.md)
- [Hizmet Sözleşmeleri Tasarlama](../designing-service-contracts.md)
