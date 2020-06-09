---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 283c8b9641dcce8b0207d3be0024b57369d125ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591468"
---
# <a name="session"></a>Oturum
Oturum örneği, oturum gerektiren bir sözleşmenin nasıl uygulanacağını gösterir. Bir oturum, birden çok işlemi gerçekleştirmek için bağlam sağlar. Bu, bir hizmetin, sonraki işlemlerin önceki bir işlemin durumunu kullanabilmesi gibi, durumu belirli bir oturumla ilişkilendirmenize olanak tanır. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır. `ICalculator`Sözleşme, çalışan bir sonuç tutarken bir dizi aritmetik işlemin gerçekleştirilmesine izin verecek şekilde değiştirilmiştir. Bu işlev, sözleşme tarafından tanımlanır `ICalculatorSession` . Bir hesaplama gerçekleştirmek için birden çok hizmet işlemi çağrıldığında hizmet, bir istemcinin durumunu tutar. İstemci, çağırarak sonucunu sıfıra getirerek geçerli sonucu alabilir `Result()` `Clear()` .  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Sözleşmenin <xref:System.ServiceModel.SessionMode> `Required` belirli bir bağlama üzerinden kullanıma sunulduğunu sağlamak için sözleşmenin, bağlamanın oturumları desteklediğini sağlar. Bağlama oturumları desteklemiyorsa, bir özel durum oluşturulur. `ICalculatorSession`Arabirim, aşağıdaki örnek kodda gösterildiği gibi, çalışan bir sonucu değiştiren bir veya daha fazla işlemin çağrılabilmesi için tanımlanır.  
  
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
  
 Hizmet, belirli bir <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> hizmet örneği bağlamını her bir gelen oturuma bağlamak için ' nı kullanır. Bu, hizmetin yerel bir üye değişkeninde her oturum için çalışan sonucu korumasına olanak tanır.  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
