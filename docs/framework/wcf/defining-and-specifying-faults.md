---
title: Hataları Tanımlama ve Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
ms.openlocfilehash: b71aaf22c98c7f8e62b5c02449a45ec75567d064
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="defining-and-specifying-faults"></a>Hataları Tanımlama ve Belirtme
SOAP hatalarının istemciye ve çift yönlü durumda, birlikte çalışabilen bir yolla bir hizmete bir istemciden hata koşulu bilgi hizmet aktarın. Bu konuda, özel hata içeriği tanımlamak ve hangi işlemleri geri dönebilirsiniz belirlemek nasıl ve ne zaman anlatılmaktadır. Bir hizmet veya çift yönlü istemci, bu hataları nasıl gönderebilir ve bir istemci veya hizmet uygulaması bu hatalarını nasıl işlediği hakkında daha fazla bilgi için bkz: [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md). Windows Communication Foundation (WCF) uygulamalarında işleme hatası genel bakış için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Genel Bakış  
 SOAP hataları olan bir işlem olduğu bildirildiğinde bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hatası türü belirtir. Bildirilmemiş SOAP hatalarının bir işlem için bir sözleşmede belirtilen değil izinlerdir. Bu konuda bu hata koşullarını tanımlamak ve istemcilerin düzgün özel SOAP hataları bildirildiğinde bu hata koşullarını işlemek için kullanabileceği hizmetiniz için hatalı sözleşme oluşturmanıza yardımcı olur. Temel görevler, sırasıyla şunlardır:  
  
1.  Bir istemci hizmeti hakkında bilmeniz gereken hata koşulları tanımlayın.  
  
2.  Bu hata koşulları için SOAP hataları özel içeriğini tanımlayın.  
  
3.  Böylece bunlar throw belirli SOAP hataları WSDL istemcilere sunulan işlemlerinizin işaretleyin.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>İstemciler hakkında bilmeniz gereken hata koşulları tanımlama  
 SOAP, belirli bir işlem için hata bilgilerinin yürütmek genel olarak açıklanan iletileri hatalarıdır. WSDL diğer işlem iletileri ile birlikte açıklanan olduğundan, istemciler bilmeniz ve, bu nedenle, bir işlem çağrılırken, bu tür hataları işlemek bekler. Ancak çünkü [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri hangi hata koşulları yönetilen kod hataları dönüştürülecek olan ve istemciye döndürülen hata koşulları ve hizmetinizden hatalar ayrı fırsatı sağlar karar yönetilen kodda yazılır bir istemciyi sahip resmi hata konuşma.  
  
 Örneğin, aşağıdaki kod örneği iki tamsayı alan ve başka bir tamsayı döndüren bir işlemi gösterir. Hatalı sözleşme tasarlarken hangi hata koşulları için istemcinizi önemli belirlemeniz gerekir böylece birden fazla özel Burada, durum. Bu durumda, hizmet algılaması gerekir <xref:System.DivideByZeroException?displayProperty=nameWithType> özel durum.  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]   
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb  
<ServiceContract> _  
Public Class CalculatorService  
    <OperationContract]> _  
    Public Function Divide(ByVal a As Integer, ByVal b As Integer) _  
       As Integer  
      If (b==0) Then   
            Throw New Exception("Division by zero!")  
      Return a/b  
    End Function  
End Class  
```  
  
 Önceki örnekte işlemi ya da sıfıra bölme için özgü özel bir SOAP hatası, matematik işlemlerine özgü ancak, birden çok hataları için birkaç bölmek için özel bilgileri içeren özel bir arıza farklı dönebilir miyim hata durumlarında, ya da hiç bir SOAP hatası.  
  
### <a name="define-the-content-of-error-conditions"></a>Hata koşulları içeriğini tanımlayın  
 Bir hata koşulu özel bir SOAP hatası usefully döndürebilen biri belirlendikten sonra sonraki adım bu hataya içeriğini tanımlayın ve içerik yapısı serileştirilebilir emin olmaktır. Önceki bölümde kod örneği, bir hata için belirli gösterir bir `Divide` olup olmadığını üzerinde başka işlemler ancak işlem, `Calculator` tek ve özel bir SOAP hatası tüm hesaplayıcı hata koşulları, istemci bilgilendirebilir sonra hizmet `Divide`dahil. Aşağıdaki kod örneği, özel bir SOAP hatası oluşturulmasını gösterir `MathFault`, hangi hatalar dahil olmak üzere tüm matematik işlemleri kullanılarak yapılan raporlama yapabilir `Divide`. Sınıf bir işlem belirtebilir sırada ( `Operation` özelliği) ve sorunu tanımlayan bir değer ( `ProblemType` özelliği), sınıf ve bu özellikleri özel bir SOAP hatası istemcisinde aktarılmasını Serileştirilebilir olmalıdır. Bu nedenle, <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> öznitelikleri seri hale getirilebilir ve mümkün olduğunca olarak çalışabilir türü ve özelliklerini yapmak için kullanılır.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Hakkında daha fazla bilgi için verilerinizi emin olmak nasıl seri hale getirilebilir bkz [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Seri hale getirme listesi için destek <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sağlar, bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Hatalı sözleşme kurmaya işareti işlemleri  
 Özel bir SOAP hatası parçası tanımlandığı gibi döndürülen bir seri hale getirilebilir veri yapısı, işlem sözleşmesi bu tür bir SOAP hatası atma olarak işaretlemek için son adımı olduğunda. Bunu yapmak için kullanın <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özniteliği ve oluşturulan özel veri türü türünü geçirin. Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.ServiceModel.FaultContractAttribute> belirtmek için öznitelik `Divide` işlemi türünde bir SOAP hatası dönebilirsiniz `MathFault`. Matematik tabanlı diğer işlemleri artık da bunlar döndürebilir belirtebilirsiniz bir `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Bir işlem birden fazla ile bu işlemi işaretleyerek birden fazla özel hata döndürdüğünü belirtebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> özniteliği.  
  
 Hatalı sözleşme işlemi uygulamanızda uygulamak için sonraki adım, konu başlığı altında açıklanan [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL ve birlikte çalışabilirlik hakkında dikkat edilecek noktalar  
 Bazı durumlarda, özellikle diğer platformlar ile birlikte çalışırken bir hataya bir SOAP iletisi görüntülenme şeklini denetlemek önemli olabilir veya biçimini WSDL meta verilerde açıklanmıştır.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Özniteliğine sahip bir <xref:System.ServiceModel.FaultContractAttribute.Name%2A> özelliği bu hata için olan meta verilerde oluşturulan WSDL hataya öğe adı izin verir.  
  
 SOAP standart göre bir hataya sahip bir `Action`, `Code`ve bir `Reason`. `Action` Tarafından denetlenen <xref:System.ServiceModel.FaultContractAttribute.Action%2A> özelliği. <xref:System.ServiceModel.FaultException.Code%2A> Özelliği ve <xref:System.ServiceModel.FaultException.Reason%2A> özelliği olan iki özelliklerini <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> genel üst sınıfı sınıfı <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. `Code` Özelliği içeren bir <xref:System.ServiceModel.FaultCode.SubCode%2A> üye.  
  
 Olmayan hataları oluşturan Hizmetleri erişirken, belirli sınırlamalarla mevcut. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Şema açıklayan ve veri sözleşmeleri ile uyumlu olan ayrıntı türleri yalnızca hataları destekler. Örneğin, yukarıda söz edildiği gibi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] XML öznitelikleri ayrıntı türlerini kullanın arıza ya da birden fazla üst düzey öğe ayrıntı bölümündeki hataları desteklemiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Hataları Gönderme ve Alma](../../../docs/framework/wcf/sending-and-receiving-faults.md)  
 [Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)  
 [Koruma Düzeylerini Anlama](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
