---
title: "WS İşlem Akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
caps.latest.revision: "43"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7043956427561e4485bdad6a98673b997bc88e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ws-transaction-flow"></a>WS İşlem Akışı
Bu örnek bir istemci Eşgüdümlü işlem kullanımını gösterir ve işlem için istemci ve sunucu seçenekleri WS-Atomic işlem veya OleTransactions protokolü kullanarak akış. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygulayan ancak kullanımını göstermek için işlemleri öznitelikli `TransactionFlowAttribute` ile **TransactionFlowOption** ne derece işlem akışı etkin belirlemek için numaralandırması. Akışlı işlem kapsamı içinde istenen işlem günlüğünü veritabanına yazılır ve Eşgüdümlü istemci işlemi tamamlanana kadar - istemci işlemi tamamlanmazsa devam ederse Web hizmeti işlemi sağlar veritabanı için uygun güncelleştirmeleri iletilmez.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 İstemci, hizmet ve işlem bağlantı başlatıldıktan sonra birkaç hizmet işlemleri erişir. Hizmet sözleşmesini gibi her biri için farklı bir ayar gösteren işlemleri ile tanımlanmış `TransactionFlowOption`.  
  
```  
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
  
 Bu, işlenmeyi oldukları sırada operations tanımlar:  
  
-   Bir `Add` işlem isteği akışlı bir işlem içermelidir.  
  
-   A `Subtract` işlem isteği akışlı bir işlem içerebilir.  
  
-   A `Multiply` işlem isteği açık QueuedDeliveryRequirements ayarı ile akışlı bir işlem değil içermelidir.  
  
-   A `Divide` işlem isteği akan işlem Java'daki üzerinden değil içermelidir bir `TransactionFlow` özniteliği.  
  
 İşlem akışını, bağlamalarla etkinleştirmek için [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) etkin özelliğinin yanı sıra uygun işlemi öznitelikler kullanılmalıdır. Bu örnekte, TCP uç noktası ve bir HTTP uç noktası bir meta veri değişimi uç noktası ek olarak hizmet yapılandırmasını gösterir. Her ikisi de sahip olan aşağıdaki bağlamaları TCP uç noktasını ve HTTP uç noktası kullan [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) etkin özelliği.  
  
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
>  Sistem tarafından sağlanan netTcpBinding transactionProtocol belirtimi sağlarken sistem tarafından sağlanan wsHttpBinding yalnızca daha birlikte çalışabilir WSAtomicTransactionOctober2004 protokolünü kullanır. OleTransactions protokolü tarafından kullanılmak üzere yalnızca kullanılabilir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemciler.  
  
 Uygulayan sınıfa için `ICalculator` arabirimi, tüm yöntemleri öznitelikli ile <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliğini `true`. Bu ayar yöntemi içinde yapılan tüm eylemler bir işlem kapsamı içinde ortaya bildirir. Bu durumda, veritabanı günlük kaydı gerçekleştirilen eylemleri içerir. İşlem isteğini akışlı bir işlem içeriyorsa eylemleri gelen işlem kapsamında meydana gelen veya yeni bir işlem kapsamı otomatik olarak oluşturulur.  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Özellik için hizmet yöntemi uygulamaları davranışını yerel tanımlar ve istemcinin yeteneği veya bir işlem akan gereksinim tanımlamıyor.  
  
```  
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
  
 İstemci, hizmet üzerinde `TransactionFlowOption` işlemlerini ayarları, istemcinin oluşturulan tanımında yansıtılır `ICalculator` arabirimi. Ayrıca, hizmetin `transactionFlow` özellik ayarları, istemci uygulama yapılandırmasında yansıtılır. İstemci taşıma ve protokolü uygun seçerek seçebilirsiniz `endpointConfigurationName`.  
  
```  
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```  
  
> [!NOTE]
>  Bu örnekte gözlenen davranışını hangi protokolü veya taşıma seçilir aynıdır.  
  
 Hizmeti bağlantısı başlatılan istemci yeni bir oluşturur `TransactionScope` hizmet işlemleri çağrıları geçici.  
  
```  
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
  
-   `Add` İstek akışları hizmetine gerekli işlem ve hizmetin Eylemler istemcinin işlem kapsamı içinde gerçekleşir.  
  
-   İlk `Subtract` istek Ayrıca hizmet için izin verilen işlem akışları ve yeniden hizmetin Eylemler istemcinin işlem kapsamı içinde gerçekleşir.  
  
-   İkinci `Subtract` isteği ile bildirilen yeni bir işlem kapsamı içinde gerçekleştirilir `TransactionScopeOption.Suppress` seçeneği. Bu istemcinin başlangıç dış işlem önler ve isteğin bir işlem hizmetine akış değil. Bu yaklaşım açıkça, çevirin ve gerekli olmadığında bir hizmet için bir işlem akan karşı korumak bir istemci sağlar. Hizmetin Eylemler yeni ve bağlantısız bir işlem kapsamı içinde gerçekleşir.  
  
-   `Multiply` İsteği akan hizmetine bir işlem istemci tanımını oluşturan çünkü `ICalculator` arabirimi içeren bir <xref:System.ServiceModel.TransactionFlowAttribute> kümesine <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   `Divide` İsteği akan hizmetine bir işlem istemci tanımını yeniden oluşturulmuş için `ICalculator` arabirim içermez bir `TransactionFlowAttribute`. Hizmetin Eylemler yeniden başka bir yeni ve bağlantısız işlem kapsamı içinde gerçekleşir.  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
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
  
 Hizmet işlemi isteklerin günlüğe yazılmasını hizmetin konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Başarılı bir yürütme sonra istemcinin işlem kapsamı tamamlar ve bu kapsamı içinde yapılan tüm eylemler uygulanır. Özellikle, not ettiğiniz 5 kayıtları hizmetin veritabanında kalıcı niteliktedir. Bu ilk 2 istemcinin işlem kapsamı içinde oluştu.  
  
 Bir özel durum istemcinin içinde herhangi bir yere oluştuysa `TransactionScope` sonra işlem tamamlanamıyor. Bu veritabanına işleminde değil, kapsam içinde kaydedilmiş kayıtları neden olur. Bu etkiyi dış tamamlamak için duyurmak yorum sonra çalıştırmak örnek tekrarlayarak gösterilebilir `TransactionScope`. Bu tür bir çalıştırmada, yalnızca son 3 eylemleri (ikinci `Subtract`, `Multiply` ve `Divide` istekleri) istemci işlemi bu akış değil çünkü kaydedilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  SQL Server Express Edition veya SQL Server yüklü olduğundan ve bağlantı dizesini hizmetin uygulama yapılandırma dosyasında doğru ayarlandığından emin olun. Örnek bir veritabanı kullanmadan çalışacak şekilde ayarlanmış `usingSql` hizmetin uygulama yapılandırma dosyasında değeri`false`  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Çapraz makine yapılandırması için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi etkinleştirin ve WCF işlemleri ağ desteğini etkinleştirmek için Windows SDK'sı WsatConfig.exe aracını kullanın. Bkz: [WS-Atomic işlem desteğini yapılandırma](http://go.microsoft.com/fwlink/?LinkId=190370) WsatConfig.exe ayarlama hakkında bilgi için.  
  
 Aynı bilgisayarda veya farklı bilgisayarlarda örneği çalıştırmak isteyip Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ işlem akışını etkinleştirmek ve etkinleştirmek için WsatConfig.exe Aracı'nı kullanmak için yapılandırmanız gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlemleri Ağ desteği.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örnek çalıştırılmasını desteklemek üzere yapılandırmak için  
  
1.  Windows Server 2003 veya Windows XP çalıştıran bir hizmeti makinede MSDTC bu yönergeleri izleyerek gelen ağ işlemlerine izin verecek biçimde yapılandırın.  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.  
  
    2.  Genişletme **Bileşen Hizmetleri**. Açık **bilgisayarlar** klasör.  
  
    3.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    4.  Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.  
  
    5.  Denetleme **ağ DTC erişimi** ve **izin gelen**.  
  
    6.  Tıklatın **Tamam**, ardından **Evet** MSDTC hizmeti yeniden başlatmak için.  
  
    7.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
2.  Windows Server 2008 veya Windows Vista çalıştıran bir hizmeti makinede MSDTC bu yönergeleri izleyerek gelen ağ işlemlerine izin verecek biçimde yapılandırın.  
  
    1.  Gelen **Başlat** menüsünde gidin **Denetim Masası**, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.  
  
    2.  Genişletme **Bileşen Hizmetleri**. Açık **bilgisayarlar** klasör. Seçin **Dağıtılmış İşlem Düzenleyicisi**.  
  
    3.  Sağ **DTC Düzenleyicisi** seçip **özellikleri**.  
  
    4.  Üzerinde **güvenlik** sekmesi, onay **ağ DTC erişimi** ve **gelene izin ver**.  
  
    5.  Tıklatın **Tamam**, ardından **Evet** MSDTC hizmeti yeniden başlatmak için.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
3.  İstemci makinesinde MSDTC giden ağ işlemlerine izin verecek biçimde yapılandırın:  
  
    1.  Gelen **Başlat** menüsünde gidin `Control Panel`, ardından **Yönetimsel Araçlar**ve ardından **Bileşen Hizmetleri**.  
  
    2.  Sağ **Bilgisayarım** seçip **özellikleri**.  
  
    3.  Üzerinde **MSDTC** sekmesini tıklatın, **Güvenlik Yapılandırması**.  
  
    4.  Denetleme **ağ DTC erişimi** ve **Gidene izin ver**.  
  
    5.  Tıklatın **Tamam**, ardından **Evet** MSDTC hizmeti yeniden başlatmak için.  
  
    6.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
