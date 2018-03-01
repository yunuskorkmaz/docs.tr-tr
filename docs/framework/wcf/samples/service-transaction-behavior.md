---
title: "Hizmet İşlem Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4c7c9c78b821f7457f193d24bae031d49b301ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-transaction-behavior"></a>Hizmet İşlem Davranışı
Bu örnek, bir istemci Eşgüdümlü işlem kullanımını ve ServiceBehaviorAttribute ve OperationBehaviorAttribute hizmet işlem davranışı denetlemek için ayarları gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) , hesap makinesi hizmetinin uygular, ancak bir veritabanı tablosu ve hesaplama işlemleri için toplam çalışan bir durum bilgisi olan gerçekleştirilen işlemler server günlüğünü korumak için genişletilir. Kalıcı yazma sunucu günlüğü tablosu için bağımlı istemci işlemi tamamlanmazsa Eşgüdümlü istemci işlem - sonuca Web hizmeti işlemi veritabanına güncelleştirmeleri iletilmez sağlar.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Tüm işlemlerini istekleriyle akışını bir işlem gerektiren hizmet sözleşmesini tanımlar:  
  
```  
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
  
 Gelen işlem akışını etkinleştirmek için hizmet sistem tarafından sağlanan wsHttpBinding kümesine transactionFlow özniteliği ile yapılandırılan `true`. Bu bağlama birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Hem başlatmadan sonra hizmet ve işlem, istemci bağlantı kapsamı içinde bu işlem birkaç hizmet işlemlerini erişir ve ardından işlem tamamlandıktan ve bağlantıyı kapatır:  
  
```  
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
  
 Hizmet üzerinde hizmet işlem davranışı etkileyen üç öznitelik ve bunu aşağıdaki yollarla yapın:  
  
-   Üzerinde `ServiceBehaviorAttribute`:  
  
    -   `TransactionTimeout` Özelliği, içinde bir işlem tamamlanmalıdır zaman aralığını belirtir. Bu örnekte 30 saniye olarak ayarlanır.  
  
    -   `TransactionIsolationLevel` Özelliği, hizmeti destekler yalıtım düzeyini belirtir. Bu, istemcinin yalıtım düzeyi eşleştirmek için gereklidir.  
  
    -   `ReleaseServiceInstanceOnTransactionComplete` Özelliği, bir işlem tamamlandığında, hizmet örneği geri dönüştürüldüğünde olup olmadığını belirtir. Ayarlayarak `false`, hizmet işlemi istekler genelinde aynı hizmet örneği bulundurur. Bu, çalışan toplam korumak için gereklidir. Varsa kümesine `true`, her eylem tamamlandıktan sonra yeni bir örneği oluşturulur.  
  
    -   `TransactionAutoCompleteOnSessionClose` Özelliği, oturumu kapattığında bekleyen işlemler tamamlandıktan olup olmadığını belirtir. Ayarlayarak `false`, tek tek işlemleri ayarlayın ya da gerekli `OperationBehaviorAttribute``TransactionAutoComplete` özelliğine `true` veya açıkça bir çağrı gerektirecek şekilde `SetTransactionComplete` işlemleri tamamlamak için yöntem. Bu örnek, her iki yaklaşımın gösterir.  
  
-   Üzerinde `ServiceContractAttribute`:  
  
    -   `SessionMode` Özelliği, hizmet uygun istekleri mantıksal bir oturuma karşılık gelen olup olmadığını belirtir. Bu hizmet için OperationBehaviorAttribute TransactionAutoComplete özelliğinin ayarlandığı işlemleri içerdiğinden `false` (çarpma ve bölme), `SessionMode.Required` belirtilmesi gerekir. Örneğin, Çarp işlemi işlemini tamamlaması değil ve bunun yerine kullanarak tamamlamak için bir sonraki çağrı bölme kullanır. `SetTransactionComplete` yöntemi; hizmeti bu işlemleri aynı oturumunda yaşanan belirlemek mümkün olması gerekir.  
  
-   Üzerinde `OperationBehaviorAttribute`:  
  
    -   `TransactionScopeRequired` Özelliği, işlem Eylemler bir işlem kapsamı içinde gerçekleştirilip gerçekleştirilmeyeceğini belirtir. Bu ayar `true` bu tüm işlemleri için örnek ve, tüm işlemleri için kendi işlem istemci akar olduğundan, Eylemler, istemci işlem kapsamı içinde gerçekleşir.  
  
    -   `TransactionAutoComplete` Özelliği, İşlenmeyen özel durumlar oluşursa işlemin hangi yöntemi yürütüldükten otomatik olarak tamamlandı olup olmadığını belirtir. Daha önce açıklandığı gibi bu ayar `true` ekleme ve çıkarma işlemleri için ancak `false` Multiply ve bölme işlemleri. Ekleme ve çıkarma işlemleri eylemlerini otomatik olarak tamamlamak, bölme için açık bir çağrı aracılığıyla, işlemlerini tamamlamadan `SetTransactionComplete` yöntemi Multiply eylemlerini tamamlanmazsa, ancak bunun yerine bağlı kullanır ve bir sonraki çağrı gibi gerektirir , Eylemleri tamamlaması için bölün.  
  
 Öznitelikli hizmet uygulaması aşağıdaki gibidir:  
  
```  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
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
  
 Hizmet işlemi isteklerin günlüğe yazılmasını hizmetin konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Çalışan toplam tutma yanı sıra unutmayın hesaplamalar hizmet örnekleri (Bu örnek için bir örnek) oluşturulmasını raporları ve işlem isteklerini bir veritabanında günlüğe kaydeder. Tüm istekleri istemcinin işlem akışı nedeniyle, tüm veritabanı işlemleri geri alınıyor bu işlemi tamamlamak için herhangi bir hata oluşur. Bu gösterilen çeşitli yollarla:  
  
-   İstemcinin çağrısına çıkışı açıklama `tx.Complete`() ve yeniden çalıştırın - bu sonuçları istemci işlemini tamamlamadan işlem kapsamı çıkılıyor.  
  
-   Out bölme hizmet işlemi çağrısı - bu sonuçları tarafından başlatılan eylemi engellemek yorum işlemin tamamlanmasını çarpma ve böylece istemcinin işlem sonunda de tamamlamak başarısız olur.  
  
-   İstemcinin işlem kapsamı içinde herhangi bir yere işlenmeyen bir özel durum - bu, bir işlem tamamlanmadan benzer şekilde istemci önler.  
  
 Bunlardan herhangi birinde bu kapsamında gerçekleştirilen işlemler hiçbiri kaydedilir ve satır sayısı veritabanına kalıcı sonucudur değil artırın.  
  
> [!NOTE]
>  Derleme işleminin bir parçası veritabanı dosyasını bin klasörüne kopyalanır. Visual Studio projeye dahil dosya yerine günlüğe kalıcı satırları izlemek için veritabanı dosyası bu kopyayı bakmak gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  SQL Server 2005 Express Edition veya SQL Server 2005'in yüklü olduğundan emin olun. Hizmetin App.config dosyasında veritabanı `connectionString` kümesi veya etkileşimleri appSettings ayarlayarak devre dışı bırakılabilir veritabanı olabilir `usingSql` değeri `false`.  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Makine genelinde örneği çalıştırırsanız, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirmek ve etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] işlemleri ağ desteği.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örnek makinelerde çalışmasını desteklemek için yapılandırmak için  
  
1.  Hizmeti makinede MSDTC gelen ağ işlemlerine izin verecek biçimde yapılandırın.  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.  
  
    2.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    3.  Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.  
  
    4.  Denetleme **ağ DTC erişimi** ve **izin gelen**.  
  
    5.  Tıklatın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
2.  Hizmet makine ve istemci makine Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dışarıda tutulan uygulamalar listesine eklemek için Windows Güvenlik Duvarı yapılandırın:  
  
    1.  Windows Güvenlik Duvarı uygulama Denetim Masası'ndan çalıştırın.  
  
    2.  Gelen **özel durumları** sekmesini tıklatın, **Program Ekle**.  
  
    3.  C:\WINDOWS\System32 klasöre göz atın.  
  
    4.  MSDTC.exe tıklatıp **açık**.  
  
    5.  Tıklatın **Tamam** kapatmak için **Program Ekle** iletişim kutusu ve tıklatın **Tamam** Windows Güvenlik Duvarı uygulamasını kapatın.  
  
3.  İstemci makinesinde MSDTC giden ağ işlemlerine izin verecek biçimde yapılandırın:  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.  
  
    2.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    3.  Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.  
  
    4.  Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.  
  
    5.  Tıklatın **Evet** MS DTC hizmetini yeniden başlatın ve ardından **Tamam**.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a>Ayrıca Bkz.
