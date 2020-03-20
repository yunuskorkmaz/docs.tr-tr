---
title: Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183358"
---
# <a name="session"></a>Oturum
Oturum örneği, oturum gerektiren bir sözleşmenin nasıl uygulanacağını gösterir. Oturum, birden çok işlem gerçekleştirmek için bağlam sağlar. Bu, bir hizmetin durumu belirli bir oturumla ilişkilendirmesine olanak tanır, böylece sonraki işlemler önceki bir işlemin durumunu kullanabilir. Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır. Sözleşme, `ICalculator` çalışan bir sonucu tutarken bir dizi aritmetik işlem yapılmasına izin verecek şekilde değiştirildi. Bu işlevsellik `ICalculatorSession` sözleşme tarafından tanımlanır. Birden çok hizmet işlemleri bir hesaplama gerçekleştirmek için çağrıldığı gibi hizmet bir istemci için durumu tutar. İstemci arayarak `Result()` geçerli sonucu alabilir ve arayarak `Clear()`sonucu sıfıra temizleyebilir.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 <xref:System.ServiceModel.SessionMode> Sözleşmenin belirli bir `Required` bağlayıcı üzerinde maruz kaldığında, bağlamanın oturumları desteklemesini sağlayacak şekilde ayarlanması. Bağlama oturumları desteklemiyorsa bir özel durum atılır. Arabirim, `ICalculatorSession` aşağıdaki örnek kodda gösterildiği gibi çalışan bir sonucu değiştiren bir veya daha fazla işlem çağrılabilen şekilde tanımlanır.  
  
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
  
 Hizmet, belirli <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> bir hizmet örneği bağlamını gelen her oturuma bağlamak için a kullanır. Bu, hizmetin her oturum için çalışan sonucu yerel bir üye değişkende korumasını sağlar.  
  
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
  
 Örneği çalıştırdığınızda, istemci sunucuya çeşitli isteklerde bulunur ve sonucu ister ve bu istek daha sonra istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
