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
ms.openlocfilehash: 67096c4531d13bc66f584c09c458c0a5a2a41c6b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260909"
---
# <a name="defining-and-specifying-faults"></a>Hataları Tanımlama ve Belirtme

SOAP hataları bir hizmetten istemciye hata koşulu bilgilerini ve çift yönlü durumda bir istemciden hizmete birlikte çalışabilen bir şekilde bir hizmeti sağlar. Bu konu, özel hata içeriğinin ne zaman ve nasıl tanımlanacağını ve hangi işlemlerin bu işlemleri döndürebileceğinizi açıklamaktadır. Bir hizmetin veya çift yönlü istemcinin bu hataları nasıl gönderebileceği ve bir istemci ya da hizmet uygulamasının bu hataları nasıl işleyeceği hakkında daha fazla bilgi için bkz. [hata gönderme ve alma](sending-and-receiving-faults.md). Windows Communication Foundation (WCF) uygulamalarında hata işlemeye genel bir bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Genel Bakış  

 Tanımlanan SOAP hataları, <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Özel BIR SOAP hata türünü belirten bir işlemin öğesine sahip olduğu olanlardır. Bildirilmemiş SOAP hataları bir işlem için sözleşmede belirtilmemiş olanlardır. Bu konu, bu hata koşullarını belirlemenize ve hizmetiniz için, istemcilerin özel SOAP hatalarıyla ilgili olarak bu hata koşullarını doğru bir şekilde işlemek için kullanabileceği bir hata sözleşmesi oluşturmanıza yardımcı olur. Temel görevler sırasıyla:  
  
1. Hizmetinizin bir istemcisinin hakkında bilgi sahibi olması gereken hata koşullarını tanımlayın.  
  
2. Bu hata koşulları için SOAP hatalarının özel içeriğini tanımlayın.  
  
3. İşlemlerinizi, oluşturdukları belirli SOAP hatalarının WSDL 'deki istemcilere gösterilmesini sağlayacak şekilde işaretleyin.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Istemcilerin hakkında bilgi sahibi olması gereken hata koşullarını tanımlama  

 SOAP hataları, belirli bir işlem için hata bilgilerini taşıyan genel olarak açıklanan iletilerdir. Bunlar, WSDL 'deki diğer işlem iletileriyle birlikte açıklandıklarından, ve bu nedenle, bir işlem çağırırken bu tür hataları işleme almayı bekler. Ancak, WCF Hizmetleri yönetilen kodda yazıldığı için, Yönetilen koddaki hangi hata koşullarının hatalara dönüştürüleceğini ve istemciye döndürülmesine karar verilmesi, istemci ile sahip olduğunuz biçimsel hata konuşmasından hizmetinize hata koşullarını ve hatalarını ayırma fırsatı sağlar.  
  
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
  
 Önceki örnekte, işlem sıfıra bölmek için özel bir SOAP hatası döndürebilir, matematik işlemlerine özel bir hata verebilir, ancak sıfıra bölmek için özel bir hata, birkaç farklı hata durumunda birden çok hata veya hiç SOAP hatası içermez.  
  
### <a name="define-the-content-of-error-conditions"></a>Hata koşullarının Içeriğini tanımlayın  

 Bir hata koşulu, özel bir SOAP hatasını tamamen döndürebilmiş bir şekilde tanımlandıktan sonra, bir sonraki adım bu hatanın içeriğini tanımlamak ve içerik yapısının serileştirildiğinden emin olmak olacaktır. Yukarıdaki bölümdeki kod örneğinde bir işleme özgü bir hata gösterilir `Divide` , ancak hizmette başka işlemler varsa, `Calculator` tek BIR özel SOAP hatası istemciye tüm hesap makinesi hata koşulları 'nın dahil olduğu konusunda bilgi verebilir `Divide` . Aşağıdaki kod örneği, `MathFault` dahil olmak üzere tüm matematik işlemlerini kullanarak yapılan hataları bildirebilen özel BIR SOAP hatası oluşturmayı gösterir `Divide` . Sınıf bir işlem ( `Operation` özellik) ve sorunu tanımlayan bir değer ( `ProblemType` özellik) belirtebilir, ancak sınıfın ve bu özelliklerin özel bir soap hatasında istemciye aktarılması için seri hale getirilebilir olması gerekir. Bu nedenle, <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> öznitelikleri tür ve özelliklerini seri hale getirilebilir ve mümkün olduğunca birlikte çalışabilir hale getirmek için kullanılır.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Verilerinizin seri hale getirilebilir olduğundan emin olmak hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](./feature-details/specifying-data-transfer-in-service-contracts.md). Sağlayan serileştirme desteğinin bir listesi için <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](./feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Hata sözleşmesini kurmak için Işlemleri işaretle  

 Özel bir SOAP hatasının parçası olarak döndürülen bir seri hale getirilebilir veri yapısı tanımlandığında, son adım işlem sözleşmenizi bu türden bir SOAP hatası oluşturan şekilde işaretlemenize neden olur. Bunu yapmak için, özniteliğini kullanın <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> ve oluşturmakta olduğunuz özel veri türünün türünü geçirin. Aşağıdaki kod örneği, <xref:System.ServiceModel.FaultContractAttribute> `Divide` işlemin türünde bir soap hatası döndürecan belirtmek için özniteliğini nasıl kullanacağınızı gösterir `MathFault` . Diğer matematik tabanlı işlemler artık, döndürebilecekleri bir de belirtebilir `MathFault` .  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Bir işlem, birden fazla özniteliğe sahip işlemi işaretleyerek birden fazla özel hata döndürdüğünü belirtebilir <xref:System.ServiceModel.FaultContractAttribute> .  
  
 Bir sonraki adım, işlem uygulamanızda hata sözleşmesinin uygulanması için [hataları gönderme ve alma](sending-and-receiving-faults.md)konusunda açıklanmaktadır.  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL ve birlikte çalışabilirlik konuları  

 Bazı durumlarda, özellikle diğer platformlarla birlikte çalışırken, bir hatanın SOAP iletisinde veya WSDL meta verilerinde açıklanma şeklini denetlemek önemli olabilir.  
  
 <xref:System.ServiceModel.FaultContractAttribute>Öznitelik, <xref:System.ServiceModel.FaultContractAttribute.Name%2A> Bu hata için meta VERILERDE oluşturulan wsdl hata öğesi adının denetimine izin veren bir özelliğe sahiptir.  
  
 SOAP standardına göre bir hata `Action` ,, `Code` ve bir olabilir `Reason` . , `Action` Özelliği tarafından denetlenir <xref:System.ServiceModel.FaultContractAttribute.Action%2A> . <xref:System.ServiceModel.FaultException.Code%2A>Özelliği ve <xref:System.ServiceModel.FaultException.Reason%2A> özelliği <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> , genel 'in üst sınıfı olan sınıfının her iki özelliğidir <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> . `Code`Özelliği bir üye içeriyor <xref:System.ServiceModel.FaultCode.SubCode%2A> .  
  
 Hata üreten hizmetlere erişirken bazı sınırlamalar vardır. WCF yalnızca şemanın açıkladığı ve veri sözleşmeleri ile uyumlu olan ayrıntı türlerine sahip hataları destekler. Örneğin, yukarıda belirtildiği gibi, WCF, ayrıntı türlerinde XML özniteliklerini kullanan hataları ya da ayrıntı bölümünde birden fazla en üst düzey öğeyle hataları desteklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](specifying-and-handling-faults-in-contracts-and-services.md)
- [Hataları Gönderme ve Alma](sending-and-receiving-faults.md)
- [Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme](how-to-declare-faults-in-service-contracts.md)
- [Koruma Düzeylerini Anlama](understanding-protection-level.md)
- [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](how-to-set-the-protectionlevel-property.md)
- [Hizmet Sözleşmelerinde Veri Aktarımını Belirtme](./feature-details/specifying-data-transfer-in-service-contracts.md)
