---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: e364b539e355f669037983813f9e6d1e0371da1f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715082"
---
# <a name="session"></a>Oturum
Oturum örneği, oturum gerektiren bir sözleşmenin nasıl uygulanacağını gösterir. Bir oturum, birden çok işlemi gerçekleştirmek için bağlam sağlar. Bu, bir hizmetin, sonraki işlemlerin önceki bir işlemin durumunu kullanabilmesi gibi, durumu belirli bir oturumla ilişkilendirmenize olanak tanır. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır. `ICalculator` sözleşmesi, çalışan bir sonuç tutarken bir dizi aritmetik işlemin gerçekleştirilmesine izin verecek şekilde değiştirilmiştir. Bu işlevsellik `ICalculatorSession` sözleşmesi tarafından tanımlanır. Bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrıldığında hizmet, bir istemcinin durumunu tutar. İstemci, `Result()` çağırarak geçerli sonucu alabilir ve `Clear()`çağırarak sonucu sıfıra temizleyebilir.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Sözleşmenin <xref:System.ServiceModel.SessionMode> `Required` olarak ayarlamak, sözleşmenin belirli bir bağlama üzerinden sunulduğunu, bağlamanın oturumları desteklediğini sağlar. Bağlama oturumları desteklemiyorsa, bir özel durum oluşturulur. `ICalculatorSession` arabirimi, aşağıdaki örnek kodda gösterildiği gibi, çalışan bir sonucu değiştiren bir veya daha fazla işlemin çağrılabilmesi için tanımlanır.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Hizmet, belirli bir hizmet örneği bağlamını her bir gelen oturuma bağlamak için bir <xref:System.ServiceModel.InstanceContextMode.PerSession> <xref:System.ServiceModel.InstanceContextMode> kullanır. Bu, hizmetin yerel bir üye değişkeninde her oturum için çalışan sonucu korumasına olanak tanır.  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 Örneği çalıştırdığınızda, istemci sunucuya birkaç istek yapar ve sonuç ister ve daha sonra istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
