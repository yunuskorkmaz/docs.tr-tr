---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183163"
---
# <a name="ws-transaction-flow"></a>WS İşlem Akışı
Bu örnek, istemci tarafından koordine edilmiş bir işlemin kullanımını ve WS-Atomik İşlem veya OleTransactions protokolünü kullanarak işlem akışı için istemci ve sunucu seçeneklerini gösterir. Bu örnek, bir hesap makinesi hizmetini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır, ancak `TransactionFlowAttribute` işlemler, işlem akışının hangi derece etkin olduğunu belirlemek için **TransactionFlowOption** numaralandırması ile birlikte kullanımı göstermek için atfedilir. Akışlı işlem kapsamında, istenen işlemlerin bir günlük bir veritabanına yazılır ve istemci koordine hareketi tamamlanana kadar devam eder - istemci hareketi tamamlanmazsa, Web hizmeti hareketi veritabanına uygun güncelleştirmeler taahhüt edilmez.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmete ve bir hareketle bağlantı başlattıktan sonra istemci çeşitli hizmet işlemlerine erişiyor. Hizmet için sözleşme, farklı bir ayar gösteren operasyonların her biri `TransactionFlowOption`ile aşağıdaki gibi tanımlanır.  

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

 Bu, işlemleri işlenecek sırayla tanımlar:  
  
- İşlem `Add` isteği, akışlı bir hareket içermelidir.  
  
- İşlem `Subtract` isteği akışlı bir hareket içerebilir.  
  
- İşlem `Multiply` isteği, açık İzin Verilmeyen ayar üzerinden akan bir hareketi içermemelidir.  
  
- İşlem `Divide` isteği, bir `TransactionFlow` öznitelik ihmal yoluyla akan bir hareket içermemelidir.  
  
 Hareket akışını etkinleştirmek için, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) uygun işlem özniteliklerine ek olarak hareketAkışı>özelliği etkinleştirilmiş bağlamalar kullanılmalıdır. Bu örnekte, hizmetin yapılandırması meta veri alışverişi bitiş noktasına ek olarak bir TCP bitiş noktası ve bir HTTP bitiş noktasını ortaya çıkarır. TCP bitiş noktası ve HTTP bitiş noktası, her ikisi de [ \<hareket Akışı>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin olan aşağıdaki bağlamaları kullanır.  
  
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
> Sistem tarafından sağlanan netTcpBinding işlemProtokolü'nün belirtimine izin vererken, sistem tarafından sağlanan wsHttpBinding yalnızca daha birlikte çalışabilir WSAtomicTransactionOctober2004 protokolünü kullanır. OleTransactions protokolü yalnızca Windows Communication Foundation (WCF) istemcileri tarafından kullanılabilir.  
  
 `ICalculator` Arabirimi uygulayan sınıf için, `true`tüm yöntemler <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> . Bu ayar, yöntem içinde gerçekleştirilen tüm eylemlerin bir işlem kapsamında gerçekleştiğini bildirir. Bu durumda, gerçekleştirilen eylemler günlük veritabanına kayıt içerir. İşlem isteği akışlı bir hareket içeriyorsa, eylemler gelen işlem kapsamında oluşur veya yeni bir hareket kapsamı otomatik olarak oluşturulur.  
  
> [!NOTE]
> Özellik, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> hizmet yöntemi uygulamalarına yerel davranış tanımlar ve istemcinin bir işlem akışı için yeteneğini veya gereksinimini tanımlamaz.  

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

 İstemcide, hizmetin `TransactionFlowOption` işlemlerdeki ayarları istemcinin oluşturulan `ICalculator` arabirimi tanımına yansıtılır. Ayrıca, hizmetin `transactionFlow` özellik ayarları istemcinin uygulama yapılandırmasında yansıtılır. İstemci uygun `endpointConfigurationName`seçerek aktarım ve protokolü seçebilirsiniz.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Hangi protokol veya aktarım seçilirse seçilsin, bu örneğin gözlenen davranışı aynıdır.  
  
 Hizmetbağlantısını başlatan istemci, hizmet işlemlerine yapılan `TransactionScope` çağrılar etrafında yeni bir yeni oluşturur.  

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

 İşlemlere yapılan aramalar aşağıdaki gibidir:  
  
- İstek, `Add` gerekli hareketi hizmete akar ve hizmetin eylemleri istemcinin hareketi kapsamında gerçekleşir.  
  
- İlk `Subtract` istek ayrıca izin verilen hareketi hizmete akar ve yine hizmetin eylemleri istemcinin hareketi kapsamında gerçekleşir.  
  
- İkinci `Subtract` `TransactionScopeOption.Suppress` istek, seçenekle birlikte bildirilen yeni bir hareket kapsamı içinde gerçekleştirilir. Bu, istemcinin ilk dış işlemini bastırır ve istek hizmete bir hareket akışı sağlamaz. Bu yaklaşım, istemcinin gerekli olmadığında bir işlemi bir hizmete akmasına karşı açıkça devre dışı bırakmasına ve korumasına olanak tanır. Hizmetin eylemleri yeni ve bağlantısız bir işlem kapsamında gerçekleşir.  
  
- `Multiply` İstemcinin oluşturulan `ICalculator` arabirim tanımı bir <xref:System.ServiceModel.TransactionFlowAttribute> dizi <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`içerdiğinden, istek hizmete bir hareket akışı sağlamaz.  
  
- Yine `Divide` istemcinin oluşturulan `ICalculator` arabirim tanımı bir `TransactionFlowAttribute`. Hizmetin eylemleri, yeni ve bağlantısız başka bir işlem kapsamında yeniden oluşur.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
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
  
 Servis işlemi isteklerinin günlüğe kaydi bölümü, hizmetin konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Başarılı bir yürütmeden sonra, istemcinin işlem kapsamı tamamlanır ve bu kapsamda gerçekleştirilen tüm eylemler taahhüt edilir. Özellikle, belirtilen 5 kayıt hizmetin veritabanında kalıcıdır. Bunlardan ilk ikisi müşterinin işlem kapsamında meydana gelmiştir.  
  
 İstemcinin herhangi bir yerinde `TransactionScope` bir özel durum oluştuysa, işlem tamamlanamaz. Bu, bu kapsamda günlüğe kaydedilen kayıtların veritabanına kaydedilmemelerine neden olur. Bu etki, dış `TransactionScope`tamamlamak için çağrı dışarı yorumlama sonra örnek çalıştırmak tekrarlayarak görülebilir. Böyle bir çalıştırmada, istemci hareketi bunlara `Subtract`akmaydığından yalnızca son 3 eylem (ikinci, istek `Multiply` ve `Divide` istekten) günlüğe kaydedilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için Windows Communication Foundation Örneklerini Oluşturma yönergelerini](../../../../docs/framework/wcf/samples/building-the-samples.md) izleyin  
  
2. SQL Server Express Edition veya SQL Server yüklediğinizden ve bağlantı dizesinin hizmetin uygulama yapılandırma dosyasında doğru şekilde ayarlandığını sağlayın. Veritabanı kullanmadan örneği çalıştırmak için, `usingSql` hizmetin uygulama yapılandırma dosyasındaki değeri`false`  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
    > [!NOTE]
    > Makineler arası yapılandırma için, Aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Koordinatörü'ne olanak sağlayın ve WCF İşlemleri ağ desteğini etkinleştirmek için Windows SDK'daki WsatConfig.exe aracını kullanın. WsatConfig.exe kurulumu hakkında daha fazla bilgi için [WS-Atomik İşlem Desteğini Yapılandırma'ya](../feature-details/configuring-ws-atomic-transaction-support.md)bakın.  
  
 Örneği ister aynı bilgisayarda ister farklı bilgisayarlarda çalıştırın, ağ hareket akışını etkinleştirmek ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig.exe aracını kullanmak için Microsoft Dağıtılmış Hareket Koordinatörü'nu (MSDTC) yapılandırmanız gerekir.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Microsoft Distributed Transaction Koordinatörü'nü (MSDTC) örneği çalıştırmak için yapılandırmak  
  
1. Windows Server 2003 veya Windows XP çalıştıran bir servis makinesinde, bu yönergeleri izleyerek gelen ağ işlemlerine izin verecek şekilde MSDTC'yi yapılandırın.  
  
    1. **Başlat** menüsünden Denetim **Masası'na,** ardından **Yönetim Araçları'na**ve ardından **Bileşen Hizmetleri'ne**gidin.  
  
    2. **Bileşen Hizmetlerini**Genişletin. **Bilgisayarlar** klasörünü açın.  
  
    3. **Bilgisayarım'ı** sağ tıklatın ve **Özellikler'i**seçin.  
  
    4. **MSDTC** sekmesinde **Güvenlik Yapılandırması'nı**tıklatın.  
  
    5. **Ağ DTC Erişimini** Denetleyin ve **GelenE İzin Verin.**  
  
    6. **TAMAM'ı**tıklatın, ardından MSDTC hizmetini yeniden başlatmak için **Evet'i** tıklatın.  
  
    7. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
2. Windows Server 2008 veya Windows Vista çalıştıran bir servis makinesinde, bu yönergeleri izleyerek gelen ağ hareketlerine izin verecek şekilde MSDTC'yi yapılandırın.  
  
    1. **Başlat** menüsünden Denetim **Masası'na,** ardından **Yönetim Araçları'na**ve ardından **Bileşen Hizmetleri'ne**gidin.  
  
    2. **Bileşen Hizmetlerini**Genişletin. **Bilgisayarlar** klasörünü açın. **Dağıtılmış Hareket Koordinatörü'nü**seçin.  
  
    3. **DTC Koordinatörü'ne** sağ tıklayın ve **Özellikler'i**seçin.  
  
    4. **Güvenlik** sekmesinde, **Ağ DTC Erişimi'ni** denetleyin ve **GelenE İzin Ver.**  
  
    5. **TAMAM'ı**tıklatın, ardından MSDTC hizmetini yeniden başlatmak için **Evet'i** tıklatın.  
  
    6. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
3. İstemci makinesinde, giden ağ hareketlerine izin verecek şekilde MSDTC'yi yapılandırın:  
  
    1. **Başlat** menüsünden, ardından `Control Panel` **Yönetim Araçları'na**ve ardından **Bileşen Hizmetleri'ne**gidin.  
  
    2. **Bilgisayarım'ı** sağ tıklatın ve **Özellikler'i**seçin.  
  
    3. **MSDTC** sekmesinde **Güvenlik Yapılandırması'nı**tıklatın.  
  
    4. **Ağ DTC Erişimini** Denetleyin ve **Gidene İzin Verin.**  
  
    5. **TAMAM'ı**tıklatın, ardından MSDTC hizmetini yeniden başlatmak için **Evet'i** tıklatın.  
  
    6. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
