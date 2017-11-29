---
title: "Hatalı Sözleşme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8fabe025e8eb2fc983094fdb78bcc37a03d0b7da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="fault-contract"></a>Hatalı Sözleşme
Hatalı sözleşme örnek, bir istemciye bir hizmetten hata bilgileri iletişim gösterilmiştir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), dahili bir özel durum bir hataya dönüştürmek için hizmetine eklenen bazı ek kod. İstemci bir hata koşulu hizmette zorla sıfıra bölme gerçekleştirmeye çalışır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hesaplayıcı sözleşme içerecek şekilde değiştirilmiş bir <xref:System.ServiceModel.FaultContractAttribute> aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
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
  
 <xref:System.ServiceModel.FaultContractAttribute> Öznitelik gösterir `Divide` işlemi türünde bir hata döndürebilir `MathFault`. Bir arıza serileştirilebilir herhangi bir türde olabilir. Bu durumda, `MathFault` bir veri sözleşmesi aşağıdaki gibidir:  
  
```  
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
  
 `Divide` Yöntemi atar bir <xref:System.ServiceModel.FaultException%601> aşağıdaki örnek kodda gösterildiği gibi özel durumu Böl olduğunda sıfır özel durum oluşur. Bu durum istemciye gönderilen bir hata ile sonuçlanır.  
  
```  
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
  
 İstemci kodu bir hata sıfıra bölme isteyerek zorlar. Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Bir hata bildirilen sıfıra bölme bakın. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 İstemci bunu uygun yakalama tarafından yapar `FaultException<MathFault>` özel durum:  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Varsayılan olarak, beklenmeyen özel durum ayrıntıları istemciye hizmetinin güvenli sınır kaçış gelen hizmet uygulaması ayrıntılarını önlemek için gönderilmez. `FaultContract`Bir sözleşmede hataları tanımlamak ve belirli türde bir özel durum iletilmesi istemci için uygun olarak işaretlemek için bir yol sağlar. `FaultException<T>`tüketicilere hataları göndermek için çalışma zamanı mekanizma sağlar.  
  
 Ancak, hata ayıklama sırasında iç hizmet hatası ayrıntılarını görmek kullanışlıdır. Daha önce açıklanan güvenli davranışı devre dışı bırakmak için her sunucuda işlenmeyen bir özel durum ayrıntıları istemciye gönderilen hata bulunması belirtebilirsiniz. Bu ayar gerçekleştirilir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> için `true`. Bu kod veya aşağıdaki örnekte gösterildiği gibi yapılandırmasında ya da ayarlayabilirsiniz.  
  
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
  
 Ayrıca, davranışı ayarlayarak hizmeti ile ilişkilendirilmelidir `behaviorConfiguration` "CalculatorServiceBehavior" yapılandırma dosyasında hizmetin özniteliği.  
  
 Bu tür hataları istemcide, genel olmayan yakalamak için <xref:System.ServiceModel.FaultException> yakalanan gerekir.  
  
 Bu davranış, yalnızca hata ayıklama amacıyla kullanılmalıdır ve hiçbir zaman üretimde etkinleştirilmiş olmalıdır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Ayrıca Bkz.
