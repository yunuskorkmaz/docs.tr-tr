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
ms.openlocfilehash: 37ded0aad547df616d2b8b73e7cb145514da080d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972363"
---
# <a name="defining-and-specifying-faults"></a>Hataları Tanımlama ve Belirtme
SOAP hataları bir hizmetten istemciye hata koşulu bilgilerini ve çift yönlü durumda bir istemciden hizmete birlikte çalışabilen bir şekilde bir hizmeti sağlar. Bu konu, özel hata içeriğinin ne zaman ve nasıl tanımlanacağını ve hangi işlemlerin bu işlemleri döndürebileceğinizi açıklamaktadır. Bir hizmetin veya çift yönlü istemcinin bu hataları nasıl gönderebileceği ve bir istemci ya da hizmet uygulamasının bu hataları nasıl işleyeceği hakkında daha fazla bilgi için bkz. [hata gönderme ve alma](../../../docs/framework/wcf/sending-and-receiving-faults.md). Windows Communication Foundation (WCF) uygulamalarında hata işlemeye genel bir bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Genel Bakış  
 Tanımlanan SOAP hataları, özel bir SOAP hata türünü belirten bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> işlemin öğesine sahip olduğu olanlardır. Bildirilmemiş SOAP hataları bir işlem için sözleşmede belirtilmemiş olanlardır. Bu konu, bu hata koşullarını belirlemenize ve hizmetiniz için, istemcilerin özel SOAP hatalarıyla ilgili olarak bu hata koşullarını doğru bir şekilde işlemek için kullanabileceği bir hata sözleşmesi oluşturmanıza yardımcı olur. Temel görevler sırasıyla:  
  
1. Hizmetinizin bir istemcisinin hakkında bilgi sahibi olması gereken hata koşullarını tanımlayın.  
  
2. Bu hata koşulları için SOAP hatalarının özel içeriğini tanımlayın.  
  
3. İşlemlerinizi, oluşturdukları belirli SOAP hatalarının WSDL 'deki istemcilere gösterilmesini sağlayacak şekilde işaretleyin.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Istemcilerin hakkında bilgi sahibi olması gereken hata koşullarını tanımlama  
 SOAP hataları, belirli bir işlem için hata bilgilerini taşıyan genel olarak açıklanan iletilerdir. Bunlar, WSDL 'deki diğer işlem iletileriyle birlikte açıklandıklarından, ve bu nedenle, bir işlem çağırırken bu tür hataları işleme almayı bekler. Ancak, WCF Hizmetleri yönetilen kodda yazıldığı için, Yönetilen koddaki hangi hata koşullarının hatalara dönüştürüleceğini ve istemciye döndürülmesine karar verilmesi, resmi hatadan hata koşullarını ve hatalarını hizmetinize ayırma fırsatı sağlar bir istemciyle yaptığınız konuşma.  
  
 Örneğin, aşağıdaki kod örneğinde iki tamsayı alan ve başka bir tamsayı döndüren bir işlem gösterilmektedir. Burada birkaç özel durum oluşturulabilir, bu nedenle hata sözleşmesini tasarlarken, istemciniz için hangi hata koşullarının önemli olduğunu belirlemelisiniz. Bu durumda, hizmet <xref:System.DivideByZeroException?displayProperty=nameWithType> özel durumu tespit etmelidir.  
  
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
  
 Önceki örnekte, işlem sıfıra bölmek için özel bir SOAP hatası döndürebilir, matematik işlemlerine özel bir hata, ancak sıfıra bölmek için özel bir hata, birkaç farklı hata için birden çok hata vardır hata durumları veya hiç SOAP hatası yok.  
  
### <a name="define-the-content-of-error-conditions"></a>Hata koşullarının Içeriğini tanımlayın  
 Bir hata koşulu, özel bir SOAP hatasını tamamen döndürebilmiş bir şekilde tanımlandıktan sonra, bir sonraki adım bu hatanın içeriğini tanımlamak ve içerik yapısının serileştirildiğinden emin olmak olacaktır. Yukarıdaki bölümde kod örneğinde bir `Divide` işleme özgü bir hata gösterilir, ancak `Calculator` hizmette başka işlemler varsa, tek bir özel SOAP hatası istemciye tüm hesap makinesi hata koşulları `Divide`hakkındabilgiverebilir.dahil edilmiştir. Aşağıdaki kod örneği, dahil olmak üzere `MathFault` `Divide`tüm matematik işlemlerini kullanarak yapılan hataları bildirebilen özel bir soap hatası oluşturmayı gösterir. Sınıf bir işlem ( `Operation` özellik) ve sorunu tanımlayan bir değer `ProblemType` (özellik) belirtebilir, ancak sınıfın ve bu özelliklerin özel bir soap hatasında istemciye aktarılması için seri hale getirilebilir olması gerekir. Bu nedenle, <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType>veöznitelikleri tür ve özelliklerini seri hale getirilebilir ve mümkün olduğunca birlikte çalışabilir hale getirmek için kullanılır. <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Verilerinizin seri hale getirilebilir olduğundan emin olmak hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sağlayan serileştirme desteğinin bir listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Hata sözleşmesini kurmak için Işlemleri işaretle  
 Özel bir SOAP hatasının parçası olarak döndürülen bir seri hale getirilebilir veri yapısı tanımlandığında, son adım işlem sözleşmenizi bu türden bir SOAP hatası oluşturan şekilde işaretlemenize neden olur. Bunu yapmak için, <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özniteliğini kullanın ve oluşturmakta olduğunuz özel veri türünün türünü geçirin. Aşağıdaki kod örneği, <xref:System.ServiceModel.FaultContractAttribute> `Divide` işlemin türünde `MathFault`bir soap hatası döndürecan belirtmek için özniteliğini nasıl kullanacağınızı gösterir. Diğer matematik tabanlı işlemler artık, döndürebilecekleri bir `MathFault`de belirtebilir.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Bir işlem, birden fazla <xref:System.ServiceModel.FaultContractAttribute> özniteliğe sahip işlemi işaretleyerek birden fazla özel hata döndürdüğünü belirtebilir.  
  
 Bir sonraki adım, işlem uygulamanızda hata sözleşmesinin uygulanması için [hataları gönderme ve alma](../../../docs/framework/wcf/sending-and-receiving-faults.md)konusunda açıklanmaktadır.  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL ve birlikte çalışabilirlik konuları  
 Bazı durumlarda, özellikle diğer platformlarla birlikte çalışırken, bir hatanın SOAP iletisinde veya WSDL meta verilerinde açıklanma şeklini denetlemek önemli olabilir.  
  
 Öznitelik, bu hata <xref:System.ServiceModel.FaultContractAttribute.Name%2A> için meta verilerde oluşturulan wsdl hata öğesi adının denetimine izin veren bir özelliğe sahiptir. <xref:System.ServiceModel.FaultContractAttribute>  
  
 SOAP standardına göre bir hata `Action` `Code`,, ve bir `Reason`olabilir. , `Action` Özelliği<xref:System.ServiceModel.FaultContractAttribute.Action%2A> tarafından denetlenir. Özelliği ve <xref:System.ServiceModel.FaultException.Reason%2A> özelliği, genel <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 'inüstsınıfıolansınıfınınherikiözelliğidir.<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> <xref:System.ServiceModel.FaultException.Code%2A> `Code` Özelliği bir<xref:System.ServiceModel.FaultCode.SubCode%2A> üye içeriyor.  
  
 Hata üreten hizmetlere erişirken bazı sınırlamalar vardır. WCF yalnızca şemanın açıkladığı ve veri sözleşmeleri ile uyumlu olan ayrıntı türlerine sahip hataları destekler. Örneğin, yukarıda belirtildiği gibi, WCF, ayrıntı türlerinde XML özniteliklerini kullanan hataları ya da ayrıntı bölümünde birden fazla en üst düzey öğeyle hataları desteklemez.  
  
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
