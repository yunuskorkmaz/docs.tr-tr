---
title: Hatalı Sözleşme
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: d8ea7010bef389b49f68c811565a641a580e230a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716954"
---
# <a name="fault-contract"></a>Hatalı Sözleşme
Hata sözleşmesi örneği, bir hizmetten istemciye hata bilgilerini nasıl ileteceğinizi gösterir. Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlar ile [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. İstemci, hizmette bir hata koşulunu zorlamak için bölme işlemini sıfıra gerçekleştirmeye çalışır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hesap makinesi sözleşmesi aşağıdaki örnek kodda gösterildiği gibi bir <xref:System.ServiceModel.FaultContractAttribute> içerecek şekilde değiştirilmiştir.  
  
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
  
 <xref:System.ServiceModel.FaultContractAttribute> özniteliği, `Divide` işleminin `MathFault`türünde bir hata döndürebileceğini belirtir. Bir hata, serileştirilemeyebilir herhangi bir türde olabilir. Bu durumda `MathFault`, aşağıdaki gibi bir veri sözleşmeniz:  
  
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
  
 Aşağıdaki örnek kodda gösterildiği gibi, sıfıra bölme özel durumu oluştuğunda `Divide` yöntemi bir <xref:System.ServiceModel.FaultException%601> özel durumu oluşturur. Bu özel durum istemciye bir hata gönderilmesine neden olur.  
  
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
  
 İstemci kodu, sıfıra bölme isteyerek bir hata vererek zorlar. Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Bir hata olarak bildirilen sıfıra göre bölmeyi görürsünüz. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 İstemci bunu uygun `FaultException<MathFault>` özel durumunu ayırarak yapar:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Varsayılan olarak, hizmet uygulamasının ayrıntılarının hizmetin güvenli sınırını aşmasını engellemek için beklenmeyen özel durumların ayrıntıları istemciye gönderilmez. `FaultContract`, bir sözleşmede hataları açıklamanıza ve istemciye iletilmek için uygun olan belirli özel durum türlerini işaretleyecek bir yol sağlar. `FaultException<T>` tüketicilere hata göndermek için çalışma zamanı mekanizmasını sağlar.  
  
 Ancak, hata ayıklama sırasında bir hizmet hatasının iç ayrıntılarını görmek faydalı olur. Daha önce açıklanan Güvenli davranışı devre dışı bırakmak için, sunucuda işlenmeyen her özel durumun ayrıntılarının istemciye gönderilen hataya dahil edileceğini belirtebilirsiniz. Bu, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> `true`ayarlanarak gerçekleştirilir. Aşağıdaki örnekte gösterildiği gibi kodda ya da yapılandırmada ayarlayabilirsiniz.  
  
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
  
 Ayrıca, yapılandırma dosyasındaki hizmetin `behaviorConfiguration` özniteliği "Hesaplatorservicebehavior" olarak ayarlanarak, davranışın hizmetle ilişkilendirilmesi gerekir.  
  
 İstemcide bu tür hataları yakalamak için genel olmayan <xref:System.ServiceModel.FaultException> yakalanmalıdır.  
  
 Bu davranış yalnızca hata ayıklama amacıyla kullanılmalıdır ve üretimde hiçbir şekilde etkinleştirilmemelidir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
