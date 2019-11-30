---
title: Hizmet Işlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: c254a7362c7bc28f4b38fc0189ae0ea763bc90cc
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568841"
---
# <a name="service-operations-wcf-data-services"></a>Hizmet Işlemleri (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, sunucuda Yöntemler sergilemek için bir veri hizmetinde hizmet işlemleri tanımlamanıza olanak sağlar. Diğer veri hizmeti kaynakları gibi hizmet işlemleri de URI 'Ler tarafından karşılanır. Hizmet işlemleri, doğrulama mantığını uygulamak, rol tabanlı güvenlik uygulamak veya özelleştirilmiş sorgulama yeteneklerini göstermek gibi bir veri hizmetinde iş mantığını kullanıma sunmasını sağlar. Hizmet işlemleri, <xref:System.Data.Services.DataService%601>türetilen veri hizmeti sınıfına eklenen yöntemlerdir. Diğer tüm veri hizmeti kaynakları gibi, hizmet işlemi metoduna parametreler sağlayabilirsiniz. Örneğin, aşağıdaki hizmet işlemi URI 'SI ( [hızlı başlangıç](quickstart-wcf-data-services.md) veri hizmetine göre) değeri `London` `city` parametresine geçirir:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

Bu hizmet işleminin tanımı aşağıdaki gibidir:

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

Veri hizmetinin kullandığı veri kaynağına doğrudan erişmek için <xref:System.Data.Services.DataService%601> <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemi tanımlama](how-to-define-a-service-operation-wcf-data-services.md).

Bir .NET Framework istemci uygulamasından bir hizmet işlemi çağırma hakkında daha fazla bilgi için bkz. [çağrı hizmeti işlemleri](calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Hizmet Işlemi gereksinimleri

Veri hizmetindeki hizmet işlemlerini tanımlarken aşağıdaki gereksinimler geçerlidir. Bir yöntem bu gereksinimleri karşılamıyorsa, veri hizmeti için bir hizmet işlemi olarak kullanıma sunulmaz.

- İşlem, veri hizmeti sınıfının bir üyesi olan bir ortak örnek yöntemi olmalıdır.

- İşlem yöntemi yalnızca giriş parametrelerini kabul edebilir. İleti gövdesinde gönderilen verilere veri hizmeti tarafından erişilemiyor.

- Parametreler tanımlanmışsa, her parametrenin türü bir ilkel tür olmalıdır. İlkel olmayan bir türdeki verilerin serileştirilmesi ve bir dize parametresine geçirilmesi gerekir.

- Yöntemin aşağıdakilerden birini döndürmesi gerekir:

  - `void` (Visual Basic`Nothing`)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Veri modelindeki veri hizmetinin sunduğu bir varlık türü.

  - Tamsayı veya dize gibi bir temel sınıf.

- Sıralama, sayfalama ve filtreleme gibi sorgu seçeneklerini desteklemek için, hizmet işlemi yöntemleri <xref:System.Linq.IQueryable%601>döndürmelidir. Sorgu seçeneklerini içeren hizmet işlemlerine yönelik istekler yalnızca <xref:System.Collections.Generic.IEnumerable%601>döndüren işlemler için reddedilir.

- Gezinti özelliklerini kullanarak ilgili varlıklara erişmeyi desteklemek için, hizmet işleminin <xref:System.Linq.IQueryable%601>döndürmesi gerekir.

- Yöntemine `[WebGet]` veya `[WebInvoke]` özniteliğiyle açıklama eklenmelidir.

  - `[WebGet]`, yönteminin bir GET isteği kullanılarak çağrılmasını sağlar.

  - `[WebInvoke(Method = "POST")]`, yöntemin bir POST isteği kullanılarak çağrılmasını sağlar. Diğer <xref:System.ServiceModel.Web.WebInvokeAttribute> Yöntemler desteklenmez.

- Bir hizmet işlemi, yöntemin dönüş değerinin bir varlık koleksiyonu yerine tek bir varlık olduğunu belirten <xref:System.Data.Services.SingleResultAttribute> ile açıklanmayabilir. Bu ayrım, yanıtın sonuç serileştirmesini ve ek gezinti özelliği traversals URI içinde temsil edilme şeklini belirler. Örneğin, AtomPub serileştirme kullanılırken, tek bir kaynak türü örneği bir giriş öğesi ve bir örnek kümesi olarak temsil edilir.

## <a name="addressing-service-operations"></a>Hizmet Işlemlerini adresleme

Bir URI 'nin ilk yol segmentine yöntemin adını yerleştirerek hizmet işlemlerine adres ekleyebilirsiniz. Örnek olarak, aşağıdaki URI `Orders` nesnelerinin <xref:System.Linq.IQueryable%601> koleksiyonunu döndüren `GetOrdersByState` işleme erişir.

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

Bir hizmet işlemi çağrılırken parametreler sorgu seçenekleri olarak sağlanır. Önceki hizmet işlemi hem dize parametresi `state` hem de bir Boole parametre `includeItems` kabul eder ve bu da ilgili `Order_Detail` nesnelerinin yanıt olarak eklenip eklenmeyeceğini gösterir.

Aşağıda, bir hizmet işlemi için geçerli dönüş türleri verilmiştir:

|Geçerli dönüş türleri|URI kuralları|
|------------------------|---------------|
|`void` (Visual Basic`Nothing`)<br /><br /> veya<br /><br /> Varlık türleri<br /><br /> veya<br /><br /> İlkel türler|URI, hizmet işleminin adı olan tek bir yol kesimi olmalıdır. Sorgu seçeneklerine izin verilmiyor.|
|<xref:System.Collections.Generic.IEnumerable%601>|URI, hizmet işleminin adı olan tek bir yol kesimi olmalıdır. Sonuç türü <xref:System.Linq.IQueryable%601> bir tür olmadığından, sorgu seçeneklerine izin verilmez.|
|<xref:System.Linq.IQueryable%601>|Hizmet işleminin adı olan yola ek olarak sorgu yolu kesimleri izin verilir. Sorgu seçeneklerine de izin verilir.|

Ek yol kesimleri veya sorgu seçenekleri, hizmet işleminin dönüş türüne bağlı olarak URI 'ye eklenebilir. Örneğin, aşağıdaki URI, ilgili `Order_Details` nesneleriyle birlikte `RequiredDate` göre azalan sırada sıralanan `Orders` nesnelerinin <xref:System.Linq.IQueryable%601> koleksiyonunu döndüren `GetOrdersByCity` işlemine erişir:

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Hizmet Işlemleri Access Control

Hizmet genelinde hizmet işlemlerinin, varlık kümesi görünürlüğü <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> yöntemi kullanılarak denetlenen şekilde, <xref:System.Data.Services.IDataServiceConfiguration> sınıfındaki <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> yöntemi tarafından denetlenir. Örneğin, veri hizmeti tanımındaki aşağıdaki kod satırı `CustomersByCity` hizmeti işlemine erişim sağlar.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Bir hizmet işleminin, temel varlık kümelerindeki erişimi kısıtlayarak gizlenmiş bir dönüş türü varsa, hizmet işlemi istemci uygulamalar tarafından kullanılamaz.

Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemi tanımlama](how-to-define-a-service-operation-wcf-data-services.md).

## <a name="raising-exceptions"></a>Özel durumları yükseltme

Veri hizmeti yürütmesinde bir özel durum her yükselttiğinizde <xref:System.Data.Services.DataServiceException> sınıfını kullanmanızı öneririz. Bunun nedeni, veri hizmeti çalışma zamanının bu özel durum nesnesinin özelliklerinin HTTP yanıt iletisine doğru bir şekilde nasıl eşleneceğini biliyor olması. Bir hizmet işleminde <xref:System.Data.Services.DataServiceException> yükselttiğinizde, döndürülen özel durum bir <xref:System.Reflection.TargetInvocationException>sarmalanır. Temel <xref:System.Data.Services.DataServiceException> kapsayan <xref:System.Reflection.TargetInvocationException>olmadan döndürmek için, <xref:System.Data.Services.DataService%601><xref:System.Data.Services.DataService%601.HandleException%2A> yöntemini geçersiz kılmanız, <xref:System.Data.Services.DataServiceException> <xref:System.Reflection.TargetInvocationException>ayıklamalısınız ve en üst düzey hata olarak, aşağıdaki örnekte olduğu gibi döndürün:

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Ayrıca bkz.

- [Durdurucular](interceptors-wcf-data-services.md)
