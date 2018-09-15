---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649373"
---
# <a name="ws-transaction-flow"></a>WS İşlem Akışı
Bu örnek, bir istemci Eşgüdümlü işlem kullanımını gösterir ve WS-Atomic işlem ya da OleTransactions protokolünü kullanarak işlem istemci ve sunucu seçeneklerini akış. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan ancak işlemleri kullanımını göstermek için öznitelikli `TransactionFlowAttribute` ile **TransactionFlowOption** ne derece işlem akışı etkin belirlemek için sabit listesi. Akışlı işlem kapsamında, istenen işlemlerin bir günlük veritabanına yazılır ve istemci işlemi tamamlanmazsa, Eşgüdümlü istemci işlemi tamamlanana kadar - devam ederse Web hizmeti işlemi sağlar ilgili güncelleştirmeleri veritabanına iletilmez.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 İstemci bağlantısına hizmet ve işlem başlatıldıktan sonra birkaç hizmet işlemleri erişir. Hizmet sözleşmesi için farklı bir ayar gösteren işlemlerin her biri ile aşağıdaki gibi tanımlıdır `TransactionFlowOption`.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 Bu, işlenmek üzere oldukları sırayla operations tanımlar:  
  
-   Bir `Add` işlem isteği akışlı bir işlem içermesi gerekir.  
  
-   A `Subtract` işlem isteği akışlı bir işlem içerebilir.  
  
-   A `Multiply` işlem isteği açık noktayla ayarı üzerinden akan bir işlem değil içermesi gerekir.  
  
-   A `Divide` işlem isteği Java'daki üzerinden akan bir işlem değil içermelidir bir `TransactionFlow` özniteliği.  
  
 İşlem akışını bağlamalarla etkinleştirmek için [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin uygun işlemi özniteliklerine ek olarak kullanılmalıdır. Bu örnekte, hizmet yapılandırmasının bir TCP uç noktası ve bir meta veri değişimi uç noktası yanı sıra bir HTTP uç noktasını kullanıma sunar. TCP uç noktası ve HTTP uç noktası, hem de aşağıdaki bağlamaları kullanın [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin.  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  Sistem tarafından sağlanan wsHttpBinding yalnızca daha birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır ancak sistem tarafından sağlanan netTcpBinding transactionProtocol belirtilmesine izin verir. Windows Communication Foundation (WCF) istemciler tarafından protokolü yalnızca kullanılabilir OleTransactions kullanın.  
  
 Uygulayan bir sınıf için `ICalculator` arabirimi, tüm yöntemleri öznitelikler atanmıştır ile <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliğini `true`. Bu ayar, bir işlem kapsamında yöntemi içinde gerçekleştirilen tüm eylemler gerçekleşmesini bildirir. Bu durumda, gerçekleştirilen eylemler için veritabanı günlük kaydı içerir. İşlem isteğini akışlı bir işlem içeriyorsa eylemleri meydana gelen işlem kapsamında veya yeni bir işlem kapsamı otomatik olarak oluşturulur.  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Özellik için hizmet yöntem uygulamaları davranışını yerel tanımlar ve istemcinin yeteneği veya gereksinim akışlı bir işlem tanımlamıyor.  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 İstemci, hizmeti üzerinde `TransactionFlowOption` işlemleri ayarları, istemcinin oluşturulan tanımı içinde yansıtılır `ICalculator` arabirimi. Ayrıca, hizmetin `transactionFlow` özellik ayarları, istemci uygulama yapılandırmasında yansıtılır. İstemci taşıma ve protokolü uygun seçerek seçebilirsiniz `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  Bu örnek gözlemlenen davranışını hangi protokolü veya aktarım seçilir aynıdır.  
  
 İstemci hizmete bağlantı tarafından başlatılan yeni bir oluşturur `TransactionScope` geçici hizmet işlemlerine çağrıları.  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 İşlem çağrıları aşağıdaki gibidir:  
  
-   `Add` Gerekli işlem hizmetine istek akışları ve hizmetin Eylemler istemcinin işlem kapsamında gerçekleşir.  
  
-   İlk `Subtract` istek, izin verilen işlem hizmetine de akar ve hizmetin Eylemler istemcinin işlem kapsamında yeniden gerçekleşir.  
  
-   İkinci `Subtract` isteği ile bildirilen yeni bir işlem kapsamı içinde gerçekleştirilir `TransactionScopeOption.Suppress` seçeneği. Bu istemcinin başlangıç dış işlem engeller ve isteğin bir işlem hizmetine akmaz. Bu yaklaşım, bir istemcinin açıkça, çevirme ve gerekli olmadığında, bir işlem hizmetine akan karşı koruma sağlar. Hizmetin Eylemler, yeni ve bağlantısız bir işlem kapsamında gerçekleşir.  
  
-   `Multiply` İsteği akan bir işlem hizmetine istemci tanımını üretilmiş çünkü `ICalculator` arabirimi içeren bir <xref:System.ServiceModel.TransactionFlowAttribute> kümesine <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   `Divide` İsteği akan bir işlem hizmetine istemci tanımını yeniden üretilmiş çünkü `ICalculator` arabirimi içermez bir `TransactionFlowAttribute`. Hizmetin Eylemler, yeni ve bağlantısız başka bir işlem kapsamında yeniden gerçekleşir.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 Hizmet işlemi isteklerini günlüğe hizmet konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Başarılı bir yürütme sonra istemcinin işlem kapsamı tamamlar ve bu kapsam içinde gerçekleştirilen tüm eylemler konusunda çok hassasız. Özellikle, not ettiğiniz 5 kaydı hizmetin veritabanında kalır. Bu ilk 2 istemci işlemi kapsamında oluştu.  
  
 Herhangi bir istemcinin içinde bir özel durum oluştuysa `TransactionScope` sonra işlem tamamlanamıyor. Bu veritabanına yürütülmesi yok o kapsam içinde kaydedilmiş kayıtları neden olur. Bu etkiyi duyurmak dış tamamlamak için yorum oluşturma sonrasında çalıştırma örneği tekrarlayarak gösterilebilir `TransactionScope`. Böyle bir alıştırmada, yalnızca son 3 eylemleri (ikinci `Subtract`, `Multiply` ve `Divide` istekleri) istemci işlemi bu akışı değil çünkü kaydedilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  SQL Server Express Edition veya SQL Server yüklü olduğundan ve bağlantı dizesini hizmetin uygulama yapılandırma dosyasında doğru ayarlandığından emin olun. Bir veritabanı kullanmadan örneği çalıştırmak için ayarlanmış `usingSql` hizmetin uygulama yapılandırma dosyasına değeri `false`  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Çapraz makine yapılandırması için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi'ni etkinleştir ve WCF işlemleri ağ desteğini etkinleştirmek için Windows SDK'sı WsatConfig.exe aracını kullanın. Bkz: [WS-Atomic işlem desteğini yapılandırma](https://go.microsoft.com/fwlink/?LinkId=190370) WsatConfig.exe hakkında bilgi.  
  
 Örneği aynı bilgisayarda veya farklı bilgisayarlarda çalıştırmak ister, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirme ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) çalıştıran destekleyecek şekilde yapılandırmak için  
  
1.  Windows Server 2003 veya Windows XP çalıştıran bir hizmeti makinede MSDTC gelen ağ işlemleri bu yönergeleri izleyerek izin verecek şekilde yapılandırın.  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.  
  
    2.  Genişletin **Bileşen Hizmetleri**. Açık **bilgisayarlar** klasör.  
  
    3.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    4.  Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.  
  
    5.  Denetleme **ağ DTC erişimi** ve **izin gelen**.  
  
    6.  Tıklayın **Tamam**, ardından **Evet** MSDTC hizmetini yeniden başlatmak için.  
  
    7.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
2.  Windows Server 2008 veya Windows Vista çalıştıran bir hizmeti makinede MSDTC gelen ağ işlemleri bu yönergeleri izleyerek izin verecek şekilde yapılandırın.  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.  
  
    2.  Genişletin **Bileşen Hizmetleri**. Açık **bilgisayarlar** klasör. Seçin **Dağıtılmış İşlem Düzenleyicisi**.  
  
    3.  Sağ **DTC Düzenleyicisi** seçip **özellikleri**.  
  
    4.  Üzerinde **güvenlik** sekmesinde, onay **ağ DTC erişimi** ve **gelene izin ver**.  
  
    5.  Tıklayın **Tamam**, ardından **Evet** MSDTC hizmetini yeniden başlatmak için.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
3.  İstemci makinesinde MSDTC giden ağ işlemleri izin verecek şekilde yapılandırın:  
  
    1.  Gelen **Başlat** menüsünde gidin `Control Panel`, ardından **Yönetimsel Araçlar**, ardından **Bileşen Hizmetleri**.  
  
    2.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    3.  Üzerinde **MSDTC** sekmesinde **Güvenlik Yapılandırması**.  
  
    4.  Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.  
  
    5.  Tıklayın **Tamam**, ardından **Evet** MSDTC hizmetini yeniden başlatmak için.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
