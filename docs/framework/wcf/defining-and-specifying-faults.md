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
ms.openlocfilehash: e2217cdac8edcab2f4b9e28484fb0758a149b72c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590597"
---
# <a name="defining-and-specifying-faults"></a>Hataları Tanımlama ve Belirtme
SOAP hatalarının istemciye ve birlikte çalışabilen bir yolla bir hizmete istemcinin çift yönlü çalışmasından hata durum bilgisini bir hizmetten aktarın. Bu konuda ele alınmıştır ne zaman ve nasıl özel hata içeriğini tanımlamak ve hangi işlemlerin döndürülmeleri belirtin. Bir hizmet ya da çift yönlü istemci bu hataların nasıl gönderebilir ve bir istemci veya hizmet uygulaması bu hataların nasıl işlediği hakkında daha fazla bilgi için bkz. [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md). Hata işleme Windows Communication Foundation (WCF) uygulamalarında genel bakış için bkz. [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Genel Bakış  
 SOAP hataları olan bir işlem olan bildirilmiş bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hatası türü belirtir. Bildirilmemiş SOAP hataları sözleşmenin bir işlem için belirtilen değil olanlardır. Bu konuda bu hata koşullarını tanımlamak ve istemcilerin düzgün bir şekilde özel SOAP hataları bildirildiğinde bu hata koşullarını işlemek için kullanabileceği hizmetiniz için bir hata sözleşme oluşturmanıza yardımcı olur. Temel görevleri sırayla şöyledir:  
  
1.  Bir istemci hizmeti hakkında bilmeniz gereken hata koşullarını tanımlayın.  
  
2.  Bu hata koşulları için SOAP hataları özel içeriği tanımlayın.  
  
3.  Böylece oluştururlar belirli bir SOAP hatası WSDL istemcilere sunulan işlemlerinizi işaretleyin.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>İstemciler hakkında bilmeniz gereken hata koşulları tanımlama  
 SOAP, belirli bir işleme hata bilgileri taşıyan herkese açık şekilde açıklandığı gibi iletileri hatalarıdır. WSDL diğer işlem iletileri birlikte açıklanan olduğundan, istemciler bilmeniz ve bu nedenle, bir işlemi çağrılırken böyle arızları beklenir. Ancak WCF hizmetleri hangi hata koşulları yönetilen kod hataları dönüştürülecek olan ve istemciye döndürülen hata koşulları ve hizmetinizdeki hataları biçimsel hata ayırmak için bir fırsat sağlar karar yönetilen kodda yazılır bir istemciye sahip konuşma.  
  
 Örneğin, aşağıdaki kod örneği, iki tamsayı alır ve başka bir tamsayı döndüren bir işlem gösterilir. Hatalı sözleşme tasarlarken hangi hata koşulları için istemcinizi önemli olduğunu belirlemeniz gerekir böylece birkaç özel durum burada atılabilir. Bu durumda, hizmet algılanmalıdır <xref:System.DivideByZeroException?displayProperty=nameWithType> özel durum.  
  
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
  
 Önceki örnekte işlemi ya da sıfıra bölme için özgü özel bir SOAP hatası, matematik işlemlerine özgü ancak, birden çok hataları için birkaç bölmek için özel bilgiler içeren özel bir hata farklı iade edebilir miyim hata durumları veya hiç bir SOAP hatası.  
  
### <a name="define-the-content-of-error-conditions"></a>Hata koşulları içeriğini tanımlama  
 Bir hata koşulu özel bir SOAP hatası usefully döndürebilen biri belirlendikten sonra sonraki adım bu hataya içeriğini tanımlamak ve içerik yapısı seri hale getirilebilir olun sağlamaktır. Önceki bölümde kod örneği için belirli bir hata gösterir bir `Divide` varsa üzerinde başka işlemler ancak işlem, `Calculator` tek ve özel bir SOAP hatası tüm hesaplayıcı hata koşulları, istemci bilgilendirebilir sonra hizmet `Divide`dahil. Aşağıdaki kod örneği, özel bir SOAP hatası oluşturulmasını gösterir `MathFault`, hangi hatalar dahil olmak üzere tüm matematik işlemleri kullanılarak yapılan rapor edebilir `Divide`. Sınıfı bir işlem belirtebilirsiniz ancak ( `Operation` özelliği) ve sorunu açıklayan bir değer ( `ProblemType` özelliği), sınıf ve bu özellikleri özel bir SOAP hatası istemciye aktarılacak öğesi Serileştirilebilir olmalıdır. Bu nedenle, <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> özniteliği, türü ve özelliklerini seri hale getirilebilir ve olarak çalışabilen yapmak için kullanılamaz.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Hakkında daha fazla bilgi için verilerinizin nasıl serileştirilebilir için bkz. [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Serileştirme bir listesi için destek <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sağlar, bkz: [veri sözleşme seri hale getirici tarafından desteklenen türleri](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Hatalı Sözleşme'kurmak için işlemleri işaretlemek  
 Özel bir SOAP hatası parçası tanımlanmadı'olarak döndüren bir seri hale getirilebilir veri yapısı işlemi sözleşmeniz, bu tür bir SOAP hatası atma olarak işaretlemek için son adımı olduğunda. Bunu yapmak için <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özniteliği ve türü, oluşturulan özel veri türü. Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.ServiceModel.FaultContractAttribute> belirtmek için öznitelik `Divide` işlemi türünde bir SOAP hatasını döndürebilir `MathFault`. Diğer matematik tabanlı işlemler şimdi de bunlar döndürebilir belirtebilirsiniz bir `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Bir işlem birden fazla bu işlemle işaretleyerek birden fazla özel hata döndürdüğünü belirtmek <xref:System.ServiceModel.FaultContractAttribute> özniteliği.  
  
 Hatalı anlaşma işlemi uygulamanızda uygulamak için bir sonraki adımda, konu başlığı altında açıklanan [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL ve birlikte çalışabilirlik değerlendirmeleri  
 Bazı durumlarda, özellikle diğer platformları ile birlikte çalışırken bir SOAP ileti bir hataya görüntülenme şeklini denetlemek önemli olabilir veya biçimini WSDL meta verilerde açıklanmıştır.  
  
 <xref:System.ServiceModel.FaultContractAttribute> Özniteliğine sahip bir <xref:System.ServiceModel.FaultContractAttribute.Name%2A> bu hata için meta verileri içinde oluşturulan WSDL hata öğe adı bir denetimin izin veren özellik.  
  
 SOAP standardına göre bir hata olabilir bir `Action`, `Code`ve `Reason`. `Action` Tarafından denetlenen <xref:System.ServiceModel.FaultContractAttribute.Action%2A> özelliği. <xref:System.ServiceModel.FaultException.Code%2A> Özelliği ve <xref:System.ServiceModel.FaultException.Reason%2A> özelliği olan iki özelliklerini <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> genel üst sınıfı olan sınıf <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. `Code` Özelliği içeren bir <xref:System.ServiceModel.FaultCode.SubCode%2A> üyesi.  
  
 Olmayan hatalar'ı oluşturan hizmetler erişirken belirli sınırlamaları vardır. Yalnızca hataları ayrıntı türleriyle şemasını tanımlayan WCF destekler ve veri sözleşmeleri ile uyumludur. Örneğin, yukarıda belirtildiği gibi WCF ayrıntı türlerini XML özniteliklerini kullanın hataları veya birden çok en üst düzey öğe ayrıntısı bölümünde hataları desteklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Hataları Gönderme ve Alma](../../../docs/framework/wcf/sending-and-receiving-faults.md)
- [Nasıl yapılır: Hizmet sözleşmelerinde hata bildirme](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)
- [Koruma Düzeylerini Anlama](../../../docs/framework/wcf/understanding-protection-level.md)
- [Nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
