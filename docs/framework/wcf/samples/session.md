---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 84f0cc34e5de0634eff2edecead08aae3a143068
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554172"
---
# <a name="session"></a>Oturum
Oturum örnek bir oturum gerektiren bir sözleşmesini uygulama gösterilmiştir. Oturum, birden çok işlemi gerçekleştirmek için bağlam sağlar. Önceki bir işlemin durumunu sonraki işlemleri kullanabilir bu durum belirli bir oturum ile ilişkilendirmek bir hizmet sağlar. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hesaplayıcı hizmet uygular. `ICalculator` Sözleşme, çalışan bir sonuç tutarken gerçekleştirilecek aritmetik işlemler kümesi izin verecek şekilde değiştirildi. Bu işlev tarafından tanımlanan `ICalculatorSession` sözleşme. Birden çok hizmet işlemleri bir hesaplama gerçekleştirmek için adlandırıldığı gibi hizmet için bir istemci durumu korur. İstemci, çağırarak geçerli sonucu alabilirsiniz `Result()` çağırarak sıfır sonucu temizleyin `Clear()`.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Ayarı <xref:System.ServiceModel.SessionMode> için sözleşmenin `Required` sözleşme üzerinden belirli bir bağlama olarak sunulduğunda oturumları bağlamayı desteklediğini sağlar. Bağlama oturumları desteklemiyorsa bir özel durum oluşturulur. `ICalculatorSession` Arabirimi tanımlanmış bir veya daha fazla işlemler çağrılabilir Öyle ki, çalışan bir sonuç değiştirir aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Hizmeti kullandığı bir <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.PerSession> gelen her oturum için belirli hizmet örneğinin bağlamı bağlamak için. Bu, yerel üye değişkenini her oturumda çalışan sonucu bir hizmet sağlar.  
  
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
  
 Örneği çalıştırdığında istemci sunucuya birden çok isteği yapan ve ardından istemci konsol penceresinde görüntüler sonucu ister. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a>Ayrıca bkz.
