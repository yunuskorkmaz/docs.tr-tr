---
title: Hatalı Sözleşme
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 5b3348f31d239d6bf7e64852ba02010115062669
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625249"
---
# <a name="fault-contract"></a>Hatalı Sözleşme
Hatalı sözleşme örnek, bir istemci bir hizmet sağlayıcısından hata bilgiler iletmek gösterilmiştir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), bazı ek kod bir hata için iç özel durum dönüştürmek için hizmet eklenir. İstemci bir hata koşulu hizmette zorlamak için sıfır ile bölme gerçekleştirmeye çalışır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
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
  
 <xref:System.ServiceModel.FaultContractAttribute> Özniteliği gösterir `Divide` işlemi türü bir hata döndürebilir `MathFault`. Seri hale getirilebilir herhangi bir türde bir hata olabilir. Bu durumda, `MathFault` bir veri anlaşması aşağıdaki gibidir:  
  
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
  
 `Divide` Yöntem bir <xref:System.ServiceModel.FaultException%601> aşağıdaki örnek kodda gösterildiği gibi özel bir bölme olduğunda sıfır özel durumun meydana gelir. Bu durum istemciye gönderilen bir hata ile sonuçlanır.  
  
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
  
 İstemci kodu, bir hata sıfıra bölme isteyerek zorlar. Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Bir hata bildirilen sıfıra bölme görürsünüz. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 İstemci uygun yakalama yapar `FaultException<MathFault>` özel durum:  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Varsayılan olarak, beklenmeyen bir özel durumların ayrıntılarını istemciye hizmetinin güvenlik sınırının kaçış gelen hizmet uygulamasının Ayrıntılar önlemek için gönderilmez. `FaultContract` bir sözleşme hataları tanımlamak ve belirli türdeki özel durumlar iletilmesi istemci için uygun olarak işaretlemek için bir yol sağlar. `FaultException<T>` tüketicilere hataları göndermek için çalışma zamanı mekanizması sağlar.  
  
 Ancak, hata ayıklama sırasında iç hizmet hatası ayrıntılarını görmek kullanışlıdır. Daha önce açıklanan güvenli davranışı kapatmak için sunucu üzerindeki her bir işlenmeyen özel durum ayrıntılarını istemciye gönderilen hata eklenmelidir belirtebilirsiniz. Bu ayarı gerçekleştirilir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> için `true`. Bunu aşağıdaki örnekte gösterildiği gibi yapılandırma veya kod ya da ayarlayabilirsiniz.  
  
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
  
 Daha fazla davranış ayarlayarak hizmeti ile ilişkilendirilmelidir `behaviorConfiguration` hizmet yapılandırma dosyasında "CalculatorServiceBehavior" özniteliği.  
  
 İstemcide, genel olmayan bu tür hataları yakalamak için <xref:System.ServiceModel.FaultException> yakalanmalıdır.  
  
 Bu davranış yalnızca hata ayıklama amacıyla kullanılmalıdır ve hiçbir zaman üretimde etkinleştirilmelidir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Ayrıca Bkz.
