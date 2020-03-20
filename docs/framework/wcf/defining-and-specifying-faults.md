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
ms.openlocfilehash: 10fc045cab995cca8d78e470d74ec9341e167308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176701"
---
# <a name="defining-and-specifying-faults"></a>Hataları Tanımlama ve Belirtme
SOAP hataları hata durumu bilgilerini bir hizmetten istemciye ve çift yönlü durumda istemciden bir hizmete birlikte çalışabilir bir şekilde iletir. Bu konu, özel hata içeriğinin ne zaman ve nasıl tanımlanabileceğini tartışır ve bunları hangi işlemlerin döndürebileceğini belirtir. Bir hizmetin veya çift yönlü istemcinin bu hataları nasıl gönderebileceği ve istemci veya hizmet uygulamasının bu hataları nasıl işlediği hakkında daha fazla bilgi [için](sending-and-receiving-faults.md)Bkz. Windows Communication Foundation (WCF) uygulamalarında hata işlemeye genel bir bakış için, [bkz.](specifying-and-handling-faults-in-contracts-and-services.md)  
  
## <a name="overview"></a>Genel Bakış  
 Beyan EDILEN SOAP hataları, bir işlemin <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hata türünü belirten bir işlemi olduğu hatalardır. Bildirilmemiş SOAP hataları, bir işlem için sözleşmede belirtilmeyen hatalardır. Bu konu, bu hata koşullarını belirlemenize ve hizmetinizin özel SOAP hataları tarafından bildirildiğinde bu hata koşullarını düzgün bir şekilde işlemek için kullanabileceği bir hata sözleşmesi oluşturmanıza yardımcı olur. Temel görevler sırayla şunlardır:  
  
1. Hizmetistemcinizin bilmesi gereken hata koşullarını tanımlayın.  
  
2. Bu hata koşulları için SOAP hatalarının özel içeriğini tanımlayın.  
  
3. Operasyonlarınızı, fırlattıkları belirli SOAP hatalarının WSDL'deki istemcilere maruz kalması için işaretleyin.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>İstemcilerin Bilmesi Gereken Hata Koşullarının Tanımlanması  
 SOAP hataları, belirli bir işlem için hata bilgisi taşıyan genel olarak açıklanan iletilerdir. WSDL'deki diğer işlem iletileriyle birlikte açıklandığından, istemciler bir işlemi çağırırken bu tür hataları bilir ve bu nedenle işlemeyi beklerler. Ancak WCF hizmetleri yönetilen kodda yazıldığından, yönetilen koddaki hangi hata koşullarının hatalara dönüştürüleceğine karar vermek ve istemciye iade etmek, hizmetinizdeki hata koşullarını ve hataları resmi hatadan ayırma fırsatı sağlar bir müşteri ile yaptığınız konuşma.  
  
 Örneğin, aşağıdaki kod örneği, iki aramsayı alan ve başka bir karşıcıyı döndüren bir işlem gösterir. Burada çeşitli özel durumlar atılabilir, bu nedenle hata sözleşmesi tasarlanırken, istemciniz için hangi hata koşullarının önemli olduğunu belirlemeniz gerekir. Bu durumda, hizmet <xref:System.DivideByZeroException?displayProperty=nameWithType> özel durumu algılamalıdır.  
  
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
    <OperationContract> _
    Public Function Divide(a As Integer, b As Integer) As Integer
        If b = 0 Then Throw New DivideByZeroException("Division by zero!")
        Return a / b
    End Function
End Class
```
  
 Önceki örnekte işlem, matematik işlemlerine özgü ancak sıfıra göre bölmeye özgü bilgiler içeren, birkaç farklı hata için birden fazla hata içeren, sıfıra bölmeye özgü özel bir SOAP hatası döndürebilir hata durumları, ya da hiç SOAP hatası.  
  
### <a name="define-the-content-of-error-conditions"></a>Hata Koşullarının İçeriğini Tanımla  
 Bir hata koşulu, özel bir SOAP hatasını yararlı bir şekilde döndürebilen bir hata olarak tanımlandıktan sonra, bir sonraki adım, bu hatanın içeriğini tanımlamak ve içerik yapısının serihale edilebilmesini sağlamaktır. Önceki bölümdeki kod örneği bir `Divide` işlem için özel bir hata gösterir, `Calculator` ancak hizmette başka işlemler varsa, tek bir özel `Divide` SOAP hatası istemciyi dahil edilen tüm hesap makinesi hata koşulları hakkında bilgilendirebilir. Aşağıdaki kod örneği, özel bir SOAP `MathFault`hatasının oluşturulmasını gösterir, bu hatalar `Divide`dahil olmak üzere tüm matematik işlemleri kullanılarak yapılan bildirebilirsiniz. Sınıf bir işlem `Operation` (özellik) ve sorunu `ProblemType` (özelliği) açıklayan bir değer belirtebilir iken, sınıf ve bu özellikleri özel bir SOAP hatası istemciye aktarılabilir serileştirilebilir olmalıdır. Bu <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> nedenle, <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> ve öznitelikleri türü ve özelliklerini serileştirilebilir ve mümkün olduğunca birlikte çalışabilir yapmak için kullanılır.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Verilerinizin serileştirilebilir olmasını nasıl sağlayacağınız hakkında daha fazla bilgi için [bkz.](./feature-details/specifying-data-transfer-in-service-contracts.md) <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sağlayan serileştirme desteğinin listesi için [bkz.](./feature-details/types-supported-by-the-data-contract-serializer.md)  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Arıza Sözleşmesini Kurmak Için İşaret İşlemleri  
 Özel bir SOAP hatasının parçası olarak döndürülen serileştirilebilir bir veri yapısı tanımlandıktan sonra, son adım, işlem sözleşmenizi bu tür bir SOAP hatası olarak işaretlemektir. Bunu yapmak için <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özniteliği kullanın ve inşa ettiğiniz özel veri türünün türünü geçirin. Aşağıdaki kod örneği, <xref:System.ServiceModel.FaultContractAttribute> `Divide` işlemin soap türünde `MathFault`bir hata döndürebileceğini belirtmek için özniteliğin nasıl kullanılacağını gösterir. Diğer matematik tabanlı işlemler artık bir `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Bir işlem, bu işlemi birden <xref:System.ServiceModel.FaultContractAttribute> fazla öznitelikle işaretleyerek birden fazla özel hata döndürebileceğini belirtebilir.  
  
 İşlem uygulamanızda hata sözleşmesini uygulamak için bir sonraki adım, [Hata Gönderme ve Alma](sending-and-receiving-faults.md)konusunda açıklanmıştır.  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL ve Birlikte Çalışabilirlik Hususlar  
 Bazı durumlarda, özellikle diğer platformlarla çalışırken, bir hatanın SOAP iletisinde görünme şeklini veya WSDL meta verilerinde tanımlanma şeklini denetlemek önemli olabilir.  
  
 Öznitelik, <xref:System.ServiceModel.FaultContractAttribute> bu <xref:System.ServiceModel.FaultContractAttribute.Name%2A> hata için meta verilerde oluşturulan WSDL hata öğesi adının denetimine izin veren bir özelliğe sahiptir.  
  
 SOAP standardına göre, bir hata `Action`bir `Code`olabilir `Reason`, a , ve bir . <xref:System.ServiceModel.FaultContractAttribute.Action%2A> Mülk `Action` tarafından kontrol ediliyor. Özellik <xref:System.ServiceModel.FaultException.Code%2A> ve <xref:System.ServiceModel.FaultException.Reason%2A> özellik, genel <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>sınıfın ana sınıfı olan sınıfın her iki özelliğidir. Tesiste `Code` bir <xref:System.ServiceModel.FaultCode.SubCode%2A> üye bulunmaktadır.  
  
 Hata oluşturan hizmet dışı hizmetlere erişirken, belirli sınırlamalar vardır. WCF yalnızca şema açıklanan ve veri sözleşmeleri ile uyumlu ayrıntı türleri ile hataları destekler. Örneğin, yukarıda belirtildiği gibi, WCF ayrıntı türlerinde XML özniteliklerini kullanan hataları veya ayrıntı bölümünde birden fazla üst düzey öğeiçeren hataları desteklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](specifying-and-handling-faults-in-contracts-and-services.md)
- [Hataları Gönderme ve Alma](sending-and-receiving-faults.md)
- [Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme](how-to-declare-faults-in-service-contracts.md)
- [Koruma Düzeylerini Anlama](understanding-protection-level.md)
- [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](how-to-set-the-protectionlevel-property.md)
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](./feature-details/specifying-data-transfer-in-service-contracts.md)
