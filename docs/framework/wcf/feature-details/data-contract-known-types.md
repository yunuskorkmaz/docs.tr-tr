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
ms.openlocfilehash: 054beab97a77bd466d2c3d8c734e37f8ded7eb62
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945268"
---
# <a name="data-contract-known-types"></a>Veri Sözleşmesi Bilinen Türler
<xref:System.Runtime.Serialization.KnownTypeAttribute> Sınıfı, serisini kaldırma sırasında dikkate alınması gereken türleri önceden belirtmenize olanak tanır. Çalışan bir örnek için, [bilinen türler](../../../../docs/framework/wcf/samples/known-types.md) örneğine bakın.  
  
 Normalde, parametreleri geçirirken ve bir istemci ile bir hizmet arasında değer döndürmelerinde, her iki uç nokta de iletilmek üzere verilerin tüm veri sözleşmelerini paylaşır. Ancak, aşağıdaki durumlarda bu durum böyle değildir:  
  
- Gönderilen veri sözleşmesi, beklenen veri sözleşmesinden türetilir. Daha fazla bilgi için, [veri sözleşmesindeki](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)devralma hakkında bölümüne bakın. Bu durumda, iletilen veriler, alıcı uç noktası tarafından beklenen veri sözleşmesine sahip değildir.  
  
- İletilecek bilgiler için, bir sınıf, yapı veya numaralandırmanın aksine, bir arabirim olduğu bildirilmiştir. Bu nedenle, arabirimi uygulayan türün gerçekten gönderildiği ve bu nedenle alıcı uç noktasının iletilen veriler için veri sözleşmesinin ön planda belirleyemediği bilinmez.  
  
- İletilecek bilgiler için belirtilen tür <xref:System.Object>. Her tür öğesinden <xref:System.Object>devralındığından ve bu türün gerçekten gönderildiği bilinmediği için, alıcı uç noktası aktarılan verilerin veri sözleşmesinin ön planda saptanamıyor. Bu, ilk öğenin özel bir durumdur: Her veri sözleşmesi, için <xref:System.Object>oluşturulan boş bir veri sözleşmesinden varsayılan olarak türetilir.  
  
- .NET Framework türlerini içeren bazı türlerin önceki üç kategoriden birinde olan üyeleri vardır. Örneğin, <xref:System.Collections.Hashtable> karma tablodaki <xref:System.Object> gerçek nesneleri depolamak için kullanır. Bu türler serileştirilirken, alıcı taraf bu üyeler için veri sözleşmesinin ön kısmına göre saptanamaz.  
  
## <a name="the-knowntypeattribute-class"></a>KnownTypeAttribute sınıfı  
 Veriler alma uç noktasına ulaştığında, WCF çalışma zamanı verileri ortak dil çalışma zamanı (CLR) türünün bir örneğine serisini kaldırma girişiminde bulunur. Seri durumdan çıkarma için örneği oluşturulan tür, önce iletinin içeriğinin uyumlu olduğu veri sözleşmesinin belirlenmesi için gelen iletiyi inceleyerek seçilir. Seri kaldırma altyapısı daha sonra ileti içeriğiyle uyumlu bir veri sözleşmesi uygulayan bir CLR türü bulmaya çalışır. Seri durumdan çıkarma altyapısının bu işlem sırasında izin verdiği aday türleri kümesi, seri hale getirici 'nin "bilinen türler" kümesi olarak adlandırılır.  
  
 Seri durumdan çıkarma altyapısının bir tür hakkında bilgi almasına imkan sağlamanın bir yolu, <xref:System.Runtime.Serialization.KnownTypeAttribute>' nı kullanmaktır. Öznitelik, tek tek veri üyelerine yalnızca tüm veri anlaşması türlerine uygulanamaz. Özniteliği, bir sınıf veya yapı olabilecek bir *dış türe* uygulanır. En temel kullanımındaki özniteliği uygulamak, bir türü "bilinen tür" olarak belirtir. Bu, dış türdeki bir nesne veya üyeleri aracılığıyla başvurulan herhangi bir nesne seri durumdan çıkarıldığı zaman bilinen türün bilinen türler kümesinin bir parçası olmasına neden olur. Aynı türde birden fazla öznitelikuygulanabilir.<xref:System.Runtime.Serialization.KnownTypeAttribute>  
  
## <a name="known-types-and-primitives"></a>Bilinen türler ve temel elemanlar  
 İlkel türler ve temel öğeler (örneğin, <xref:System.DateTime> ve <xref:System.Xml.XmlElement>) olarak değerlendirilen belirli türler her zaman "biliniyor" ve bu mekanizmaya hiç eklenmemek zorunda değildir. Ancak, temel türlerin dizileri açıkça eklenmelidir. Çoğu koleksiyon dizilere eşit kabul edilir. (Genel olmayan koleksiyonlar diziler <xref:System.Object>için eşdeğer olarak kabul edilir). Temel elemanlar, ilkel diziler ve basit koleksiyonlar kullanmanın bir örneği için bkz. örnek 4.  
  
> [!NOTE]
> Diğer temel türlerin aksine, <xref:System.DateTimeOffset> yapı varsayılan olarak bilinen bir tür değildir, bu nedenle bilinen türler listesine el ile eklenmelidir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örneklerde kullanılan <xref:System.Runtime.Serialization.KnownTypeAttribute> sınıf gösterilmektedir.  
  
#### <a name="example-1"></a>Örnek 1  
 Devralma ilişkisine sahip üç sınıf vardır.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 Aşağıdaki `CompanyLogo` sınıf seri hale getirilebilir, ancak `ShapeOfLogo` üye bir `CircleType` ya da bir `TriangleType` nesne olarak ayarlandıysa seri durumdan çıkarılamıyor, çünkü seri kaldırma altyapısı veri sözleşme adlarıyla herhangi bir türü tanımaz " Daire "veya" üçgen. "  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 `CompanyLogo` Türü yazmanın doğru yolu aşağıdaki kodda gösterilmiştir.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Dış tür `CompanyLogo2` seri durumdan çıkarılabildiğinde, seri durumdan çıkarma motoru `CircleType` ve `TriangleType` ile ilgili olarak, "daire" ve "üçgen" veri sözleşmeleri için eşleşen türleri bulabilir.  
  
#### <a name="example-2"></a>Örnek 2  
 Aşağıdaki örnekte, her ikisi de `CustomerTypeA` ve `CustomerTypeB` `Customer` veri sözleşmesine sahip olsa bile, her bir seri hale `CustomerTypeB` geldiğinde bir `PurchaseOrder` örneği oluşturulur, çünkü yalnızca `CustomerTypeB` seri durumdan çıkarma altyapısı.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnekte, bir <xref:System.Collections.Hashtable> , içeriğini dahili olarak <xref:System.Object>depolar. Bir karma tablonun serisini başarıyla kaldırmak için, seri durumdan çıkarma altyapısının, burada oluşabilecek olası türler kümesini bilmeleri gerekir. Bu durumda, `Book` yalnızca ve `Magazine` nesnelerinin üzerinde depolandıkları için `Catalog`, bu, <xref:System.Runtime.Serialization.KnownTypeAttribute> öznitelik kullanılarak eklenmeleri durumunda olduğunu biliyoruz.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Örnek 4  
 Aşağıdaki örnekte, bir veri sözleşmesi numarayı ve numara üzerinde gerçekleştirilecek bir işlemi depolar. Veri üyesi tamsayı, tamsayılar dizisi veya tamsayılar içeren bir <xref:System.Collections.Generic.List%601> dize olabilir. `Numbers`  
  
> [!CAUTION]
>  Bu, yalnızca SVCUTIL ise istemci tarafında çalışır. EXE, bir WCF proxy oluşturmak için kullanılır. SVCUTIL. EXE, bilinen türler dahil olmak üzere hizmetten meta verileri alır. Bu bilgiler olmadan, istemci türlerin serisini kaldıramıyor.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Bu uygulama kodudur.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Bilinen türler, devralma ve arabirimler  
 Bilinen bir tür `KnownTypeAttribute` özniteliği kullanılarak belirli bir türle ilişkilendirildiğinde, bilinen tür aynı zamanda bu türün türetilmiş tüm türleri ile ilişkilendirilir. Örneğin, aşağıdaki koda bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `AdditionalShape` `KnownTypeAttribute` `Square` `Circle` Temel sınıf ( `DoubleDrawing` )zatenbuözniteliklerinuygulanmışolmasınedeniyle,sınıfı,'ınvealan`Drawing`içinde özniteliğini gerektirmez.  
  
 Bilinen türler, arabirimler değil yalnızca sınıflar ve yapılar ile ilişkilendirilebilir.  
  
## <a name="known-types-using-open-generic-methods"></a>Açık genel yöntemler kullanan bilinen türler  
 Bilinen bir tür olarak genel bir tür eklemek gerekebilir. Ancak açık genel tür `KnownTypeAttribute` özniteliğe parametre olarak geçirilemez.  
  
 Bu sorun, alternatif bir mekanizma kullanılarak çözülebilir: Bilinen türler koleksiyonuna eklemek üzere türlerin bir listesini döndüren bir yöntem yazın. Yöntemin adı, daha sonra bazı kısıtlamalar nedeniyle `KnownTypeAttribute` özniteliğe dize bağımsız değişkeni olarak belirtilir.  
  
 Yöntemin, `KnownTypeAttribute` özniteliğin uygulandığı türde olması gerekir, statik olması gerekir, parametre içermemelidir ve ' <xref:System.Collections.IEnumerable> nin <xref:System.Type>atanabileceği bir nesne döndürmesi gerekir.  
  
 Özniteliği, `KnownTypeAttribute` aynı türde gerçek türler içeren bir yöntem adı `KnownTypeAttribute` ve özniteliklerle birleştiremezsiniz. Ayrıca, aynı türde bir yöntem adına sahip `KnownTypeAttribute` birden fazla tane uygulayamazsınız.  
  
 Aşağıdaki sınıfa bakın.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 Alan, `ColorDrawing` herikisi`BlackAndWhiteDrawing`de genel bir sınıftan devraldığı bir genel sınıfın ve genel sınıfın örneklerini içerir. `Drawing` `theDrawing` Normalde, her ikisi de bilinen türlere eklenmelidir, ancak öznitelikler için geçerli sözdizimi şu değildir.  
  
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
  
 Yukarıdaki yapılandırma dosyasında, çağrılan `MyCompany.Library.Shape` bir veri anlaşması türü bilinen bir tür olacak `MyCompany.Library.Circle` şekilde bildirilmiştir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Bilinen Türler](../../../../docs/framework/wcf/samples/known-types.md)
- [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)
