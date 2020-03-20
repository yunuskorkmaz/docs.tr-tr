---
title: Hatalı Sözleşme
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: c8e93f73d150132c9d6750b81ba2ade944808d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183661"
---
# <a name="fault-contract"></a>Hatalı Sözleşme
Hata Sözleşmesi örneği, bir hizmetten istemciye hata bilgilerinin nasıl iletilebildiğini gösterir. Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlarla [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır. İstemci, hizmette hata koşulunu zorlamak için bölmeyi sıfıra kadar gerçekleştirmeye çalışır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hesap makinesi sözleşmesi, aşağıdaki <xref:System.ServiceModel.FaultContractAttribute> örnek kodda gösterildiği gibi bir sözleşme içerecek şekilde değiştirilmiştir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 Öznitelik, <xref:System.ServiceModel.FaultContractAttribute> `Divide` işlemin bir tür `MathFault`hatası döndürebileceğini gösterir. Bir hata seri hale getirilebilen herhangi bir türde olabilir. Bu durumda, `MathFault` aşağıdaki gibi bir veri sözleşmesi:  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 Yöntem, `Divide` aşağıdaki <xref:System.ServiceModel.FaultException%601> örnek kodda gösterildiği gibi sıfır özel durum bölme sayılsa özel bir durum oluşturur. Bu özel durum, istemciye bir hata gönderilmesine neden olur.  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 İstemci kodu sıfır a bölme isteyerek bir hata zorlar. Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Bölünmenin sıfır adedinin bir hata olarak rapor edildiğini görüyorsunuz. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 İstemci bunu uygun `FaultException<MathFault>` özel durumu yakalayarak yapar:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Varsayılan olarak, hizmet uygulamasının ayrıntılarının hizmetin güvenli sınırından kaçmasını önlemek için beklenmeyen özel durumların ayrıntıları istemciye gönderilmez. `FaultContract`bir sözleşmedeki hataları açıklamak ve istemciye iletim için uygun olarak belirli türde özel durumları işaretlemek için bir yol sağlar. `FaultException<T>`tüketicilere hata göndermek için çalışma süresi mekanizmasını sağlar.  
  
 Ancak, hata ayıklama yaparken bir hizmet hatasıiç ayrıntılarını görmek yararlıdır. Daha önce açıklanan güvenli davranışı kapatmak için, sunucudaki işlenmemiş her özel durum ayrıntılarının istemciye gönderilen hataya dahil edilmesi gerektiğini belirtebilirsiniz. Bu ayarlayarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> `true`gerçekleştirilir. Aşağıdaki örnekte gösterildiği gibi kodolarak veya yapılandırmada ayarlayabilirsiniz.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Ayrıca, yapılandırma dosyasındaki hizmetin özniteliğini "CalculatorServiceBehavior" olarak ayarlayarak `behaviorConfiguration` hizmetle ilişkili olması gerekir.  
  
 İstemci üzerinde bu tür hataları yakalamak <xref:System.ServiceModel.FaultException> için, olmayan genel yakalanmış olmalıdır.  
  
 Bu davranış yalnızca hata ayıklama amacıyla kullanılmalı ve üretimde asla etkinleştirilmemelidir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
