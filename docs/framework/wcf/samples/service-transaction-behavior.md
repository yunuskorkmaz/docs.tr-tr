---
title: Hizmet İşlem Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: dafc75c9db0dfe9b51c7425a269c166182bbcc87
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843038"
---
# <a name="service-transaction-behavior"></a>Hizmet İşlem Davranışı
Bu örnek, bir istemci Eşgüdümlü işlem kullanımı ve ServiceBehaviorAttribute ve OperationBehaviorAttribute hizmet işlem davranışı denetlemek için ayarları gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) , hesaplayıcı hizmet uygular, ancak gerçekleştirilen işlemlerin bir veritabanı tablosu ve hesap makinesi işlemleri için toplam çalışan bir durum bilgisi olan bir sunucu günlüğü korumak için genişletilir. Sunucu günlüğü tablosu kalıcı Yazar bağımlı istemci işlemi tamamlanmazsa, bir istemci Eşgüdümlü işlem - sonucunu Web hizmeti işlemi güncelleştirmeleri veritabanına kaydedilmiş olmamasını sağlar.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Tüm işlemlerin isteklerle akışını bir işlem gerektiren hizmet sözleşmesini tanımlar:  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 Gelen işlem akışını etkinleştirmek için hizmeti sistem tarafından sağlanan wsHttpBinding kümesine transactionFlow özniteliğine sahip yapılandırılmış `true`. Bu bağlama birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Her iki başlatmadan sonra hizmet ve işlem, istemci bağlantısı bu işlemin kapsamı içinde birkaç hizmet işlemleri erişen hareketi tamamlar ve bağlantıyı kapatır:  
  
```csharp
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 Hizmet, hizmet işlem davranışı etkileyen üç öznitelikleri vardır ve aşağıdaki yollarla bunu:  
  
-   Üzerinde `ServiceBehaviorAttribute`:  
  
    -   `TransactionTimeout` Özelliği, içinde bir işlem tamamlamalısınız süreyi belirtir. Bu örnekte, 30 saniye olarak ayarlanır.  
  
    -   `TransactionIsolationLevel` Özellik hizmetinin desteklediği yalıtım düzeyini belirtir. Bu, istemcinin yalıtım düzeyi eşleştirmek için gereklidir.  
  
    -   `ReleaseServiceInstanceOnTransactionComplete` Özelliği, bir işlem tamamlandığında, hizmet örneği geri olup olmadığını belirtir. Ayarlayarak `false`, hizmetin işlemi istekler genelinde aynı hizmet örneği tutar. Değişen Toplam korumak için gereklidir. Varsa kümesine `true`, her eylem tamamlandıktan sonra yeni bir örneği oluşturulur.  
  
    -   `TransactionAutoCompleteOnSessionClose` Özelliği, bekleyen işlemler oturumu kapattığında tamamlanıp tamamlanmadığını belirtir. Ayarlayarak `false`, tek işlemler için ayarlayın ya da gerekli <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> özelliğini `true` veya açıkça bir çağrı gerektirecek şekilde <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> işlemleri tamamlamak için yöntemi. Bu örnek iki yaklaşımı gösterir.  
  
-   Üzerinde `ServiceContractAttribute`:  
  
    -   `SessionMode` Özelliği, hizmet, mantıksal bir oturuma uygun istekleri ilişkilendiren olup olmadığını belirtir. Bu hizmet işlemleri için OperationBehaviorAttribute TransactionAutoComplete özelliğinin ayarlandığı içerdiğinden `false` (çarpma ve bölme), `SessionMode.Required` belirtilmesi gerekir. Örneğin, birden çok kez işlemi kendi işlem tamamlanmaz ve bunun yerine kullanarak tamamlamak için bir sonraki çağrı sırasında bölme kullanır `SetTransactionComplete` yöntemi; hizmeti bu işlemleri aynı oturumunda oluşan belirlemek mümkün olması gerekir.  
  
-   Üzerinde `OperationBehaviorAttribute`:  
  
    -   `TransactionScopeRequired` Özelliği, işlem eylemlerini bir işlem kapsamında yürütülüp yürütülmeyeceğini belirtir. Bu ayar `true` bu tüm işlemler için örnek ve istemci için tüm işlemleri, işlem akışları çünkü bu istemci işlemi kapsamında eylemler gerçekleşir.  
  
    -   `TransactionAutoComplete` Özelliği, İşlenmeyen özel durumlar oluşursa yöntemi yürütür işlem otomatik olarak tamamlanıp tamamlanmadığını belirtir. Daha önce açıklandığı gibi bu ayar `true` ekleme ve çıkarma işlemlerinde ancak `false` Multiply ve bölme işlemleri için. Eylemlerini otomatik olarak ekleme ve çıkarma işlemleri tamamlamak, açık bir çağrı aracılığıyla eylemlerini Böl tamamlandıktan `SetTransactionComplete` yöntemi Multiply eylemlerini tamamlamak değil ancak bunun yerine bağlı kullanır ve bir sonraki çağrı gibi gerektirir Bölme, işlemleri tamamlamak için kullanılır.  
  
 Öznitelikli hizmet uygulaması aşağıdaki gibidir:  
  
```csharp
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 Hizmet işlemi isteklerini günlüğe hizmet konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Değişen Toplam tutmanın yanı sıra dikkat edin, hesaplamaların hizmet örnekleri (Bu örnek için bir örnek) oluşturulmasını raporları ve işlem istekleri bir veritabanına kaydeder. Tüm isteklerin istemcinin işlem akış olduğundan, bu işlemi tamamlamak için herhangi bir hata geri alınan veritabanı işlemlerinin tümünde sonuçlanır. Bu gösterildiği çeşitli şekillerde:  
  
-   İstemcinin çağrısına yorum `tx.Complete`() ve yeniden çalıştır - bu sonuçları istemci kendi işlem tamamlamadan işlem kapsamı çıkılıyor.  
  
-   Açıklama çıkış bölme hizmet işlemi çağrısı - eylemi tarafından başlatılan bu sonuçları önlemek çarpma işleminin tamamlanmasını ve bu nedenle istemcinin işlem sonuçta da tamamlamak başarısız olur.  
  
-   İstemci işlem kapsamı içindeki herhangi bir yere işlenmeyen bir özel durum - bu benzer şekilde istemci kendi işlem önler.  
  
 Bu kapsam içinde gerçekleştirilen işlemleri hiçbiri kararlıyız ve veritabanında satır sayısı kalıcı bunlardan herhangi birinde sonucudur değil artırın.  
  
> [!NOTE]
>  Yapı işleminin bir parçası olarak veritabanı dosyasını bin klasörüne kopyalanır. Bu Visual Studio projesinde bulunan dosya yerine günlüğe kalıcı satırları gözlemlemek için veritabanı dosyasının kopyasını gözden geçirmeniz gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  SQL Server 2005 Express Edition veya SQL Server 2005'in yüklü olduğundan emin olun. Hizmetin App.config dosyasında, veritabanı `connectionString` kümesi veya etkileşimler appSettings ayarlayarak devre dışı bırakılabilir veritabanı `usingSql` değerini `false`.  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Makineler arasında örneği çalıştırırsanız, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirme ve Windows Communication Foundation (WCF) işlemleri ağ etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir destekler.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örnek makinelerde çalışan destekleyecek şekilde yapılandırmak için  
  
1.  Hizmeti makinede MSDTC gelen ağ işlemleri izin verecek şekilde yapılandırın.  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.  
  
    2.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    3.  Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.  
  
    4.  Denetleme **ağ DTC erişimi** ve **izin gelen**.  
  
    5.  Tıklayın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
2.  Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) hariç tutulan uygulamalar listesine eklemek için Windows Güvenlik Duvarı hizmeti makinesi ve istemci makine üzerinde yapılandırın:  
  
    1.  Windows Güvenlik Duvarı uygulaması Denetim Masası'ndan çalıştırın.  
  
    2.  Gelen **özel durumları** sekmesinde **Program Ekle**.  
  
    3.  C:\WINDOWS\System32 klasöre göz atın.  
  
    4.  MSDTC.exe seçip tıklayın **açık**.  
  
    5.  Tıklayın **Tamam** kapatmak için **Program Ekle** iletişim kutusu seçeneğine tıklayıp **Tamam** Windows Güvenlik Duvarı uygulamasını kapatın.  
  
3.  İstemci makinesinde MSDTC giden ağ işlemleri izin verecek şekilde yapılandırın:  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.  
  
    2.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    3.  Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.  
  
    4.  Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.  
  
    5.  Tıklayın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
