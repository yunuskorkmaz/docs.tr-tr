---
title: WS İşlem Akışı
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 781934e9ab27f761e71841c2edc509f9b8022aa7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094754"
---
# <a name="ws-transaction-flow"></a>WS İşlem Akışı
Bu örnek, WS-Atomik Işlem veya OleTransactions protokolünü kullanarak, istemci ile eşgüdümlü bir işlemin ve işlem akışı için istemci ve sunucu seçeneklerinin kullanımını gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetini temel alır ancak işlemler, işlem akışının ne derece etkin olduğunu belirlemek için **TransactionFlowOption** numaralandırmasıyla `TransactionFlowAttribute` kullanımını göstermeye yönelik olarak belirlenir. Akışlı işlemin kapsamı içinde, istenen işlemlerin bir günlüğü veritabanına yazılır ve istemci ile Eşgüdümlü işlem tamamlanana kadar devam etmez-istemci işlemi tamamlanmazsa, Web hizmeti işlemi veritabanına yönelik uygun güncelleştirmeler yürütülmedi.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet ve bir işlem bağlantısı başlattıktan sonra istemci çeşitli hizmet işlemlerine erişir. Hizmet sözleşmesi, `TransactionFlowOption`farklı bir ayar gösteren işlemlerden her biriyle aşağıdaki gibi tanımlanır.  

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

 Bu işlem, işlemleri işlenecek sırada tanımlar:  
  
- `Add` işlem isteği bir akışlı işlem içermelidir.  
  
- Bir `Subtract` işlem isteği, bir akışlı işlem içerebilir.  
  
- `Multiply` işlem isteği açık NotAllowed ayarı aracılığıyla bir akışlı işlem içermemelidir.  
  
- Bir `Divide` işlem isteği, bir `TransactionFlow` özniteliği atlanmaz bir akışlı işlem içermemelidir.  
  
 İşlem akışını etkinleştirmek için, [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkinleştirilmiş bağlamaların uygun işlem özniteliklerine ek olarak kullanılması gerekir. Bu örnekte, hizmetin yapılandırması bir TCP uç noktası ve bir meta veri değişimi uç noktasına ek olarak bir HTTP uç noktası sunar. TCP uç noktası ve HTTP uç noktası, her ikisi de [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) özelliği etkin olan aşağıdaki bağlamaları kullanır.  
  
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
> Sistem tarafından sunulan netTcpBinding, transactionProtocol belirtimine izin verir, ancak sistem tarafından sunulan wsHttpBinding yalnızca daha fazla çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır. OleTransactions protokolü yalnızca Windows Communication Foundation (WCF) istemcileri tarafından kullanılabilir.  
  
 `ICalculator` arabirimini uygulayan sınıf için tüm yöntemler, `true`olarak ayarlanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ile ilişkilidir. Bu ayar, yöntem içinde gerçekleştirilen tüm eylemlerin bir işlemin kapsamı içinde gerçekleştiğini bildirir. Bu durumda, gerçekleştirilen eylemler günlük veritabanına kayıt içerir. İşlem isteği bir akışlı işlem içeriyorsa, eylemler gelen işlemin kapsamı içinde veya yeni bir işlem kapsamı otomatik olarak oluşturulur.  
  
> [!NOTE]
> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği, yerel davranışı hizmet yöntemi uygulamalarına göre tanımlar ve istemcinin bir işlemi akışa alma gereksinimini tanımlamaz.  

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

 İstemcisinde, hizmetin işlemler üzerindeki `TransactionFlowOption` ayarları, istemcinin `ICalculator` arabiriminin oluşturulan tanımına yansıtılır. Ayrıca, hizmetin `transactionFlow` özellik ayarları istemcinin uygulama yapılandırmasına yansıtılır. İstemci, uygun `endpointConfigurationName`seçerek taşıma ve Protokolü seçebilir.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Bu örneğin gözlemlenen davranışı, hangi protokol veya taşımanın seçildiğine bakılmaksızın aynıdır.  
  
 Hizmet bağlantısını başlatmaktan, istemci, hizmet işlemlerine yapılan çağrılar etrafında yeni bir `TransactionScope` oluşturur.  

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

 İşlemlere yapılan çağrılar aşağıdaki gibidir:  
  
- `Add` isteği, gerekli işlemi hizmete akar ve hizmetin eylemleri, istemci işleminin kapsamı içinde gerçekleşir.  
  
- İlk `Subtract` isteği Ayrıca izin verilen işlemi hizmete akar ve hizmetin eylemleri istemci işleminin kapsamında oluşur.  
  
- İkinci `Subtract` isteği, `TransactionScopeOption.Suppress` seçeneğiyle belirtilen yeni bir işlem kapsamı içinde gerçekleştirilir. Bu, istemcinin ilk dış işlemini bastırır ve istek, hizmete bir işlem akışı yapmaz. Bu yaklaşım, bir istemcinin, gerekli olmadığında bir hizmetin bir işlemin akışını açıkça geri almasına ve korumasına olanak tanır. Hizmetin eylemleri, yeni ve bağlı olmayan bir işlemin kapsamı içinde gerçekleşir.  
  
- `Multiply` isteği, istemcinin `ICalculator` arabiriminin oluşturulan tanımı <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`olarak ayarlanmış bir <xref:System.ServiceModel.TransactionFlowAttribute> içerdiğinden hizmete bir işlem Flow.  
  
- `Divide` isteği, istemcinin `ICalculator` arabiriminin oluşturulan tanımı bir `TransactionFlowAttribute`içermediği için bir işlemi hizmete Flow. Hizmetin eylemleri, başka bir yeni ve bağlı olmayan işlemin kapsamı içinde gerçekleşir.  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
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
  
 Hizmet işlemi isteklerinin günlüğe kaydedilmesi, hizmetin konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Başarılı bir yürütme sonrasında, istemcinin işlem kapsamı tamamlanır ve bu kapsam içinde gerçekleştirilen tüm eylemler işlenir. Özellikle, belirtilen 5 kayıt hizmetin veritabanında kalıcı hale getirilir. Bunların ilk 2 ' nin, istemci işleminin kapsamı içinde meydana geldi.  
  
 İstemci `TransactionScope` bir özel durum oluştuysa, işlem tamamlanamaz. Bu, bu kapsam içinde günlüğe kaydedilen kayıtların veritabanına uygulanmamasını sağlar. Bu efekt, dış `TransactionScope`tamamlamaya yönelik çağrının yorum yapıldıktan sonra örnek çalıştırmayı tekrarlayarak gözlemlenebilir. Bu tür bir çalıştırmada, istemci işlemi bu işlemlere akmadığı için yalnızca son 3 eylem (ikinci `Subtract`, `Multiply` ve `Divide` istekleri) günlüğe kaydedilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü derlemek Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md) konusundaki yönergeleri izleyin  
  
2. SQL Server Express Edition veya SQL Server yüklediğinizden ve bağlantı dizesinin hizmetin uygulama yapılandırma dosyasında doğru şekilde ayarlandığından emin olun. Örneği bir veritabanı kullanmadan çalıştırmak için, hizmetin uygulama yapılandırma dosyasında `usingSql` değerini `false` olarak ayarlayın  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
    > [!NOTE]
    > Platformlar arası yapılandırma için aşağıdaki yönergeleri kullanarak Dağıtılmış İşlem Düzenleyicisi etkinleştirin ve Windows SDK WCF Işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanın. WsatConfig. exe ' yi ayarlama hakkında daha fazla bilgi için bkz. [WS Atomik Işlem desteğini yapılandırma](../feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Örneği aynı bilgisayarda veya farklı bilgisayarlarda çalıştırdığınız gibi, ağ işlem akışını etkinleştirmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırmanız ve WCF işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanmanız gerekir.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) örneğini çalıştırmayı destekleyecek şekilde yapılandırmak için  
  
1. Windows Server 2003 veya Windows XP çalıştıran bir hizmet makinesinde, bu yönergeleri izleyerek MSDTC 'yi gelen ağ işlemlerine izin verecek şekilde yapılandırın.  
  
    1. **Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.  
  
    2. **Bileşen Hizmetleri**' ni genişletin. **Bilgisayarlar** klasörünü açın.  
  
    3. **Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.  
  
    4. **MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.  
  
    5. **Ağ DTC erişimini** denetleyin ve **gelen erişime izin verin**.  
  
    6. **Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.  
  
    7. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
2. Windows Server 2008 veya Windows Vista çalıştıran bir hizmet makinesinde, bu yönergeleri izleyerek MSDTC 'yi gelen ağ işlemlerine izin verecek şekilde yapılandırın.  
  
    1. **Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.  
  
    2. **Bileşen Hizmetleri**' ni genişletin. **Bilgisayarlar** klasörünü açın. **Dağıtılmış işlem Düzenleyicisi**seçin.  
  
    3. **DTC Düzenleyicisi** ' ne sağ tıklayıp **Özellikler**' i seçin.  
  
    4. **Güvenlik** sekmesinde, **Ağ DTC erişimi** ' ni ve **gelen izin ver**' i işaretleyin.  
  
    5. **Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.  
  
    6. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
3. İstemci makinesinde, giden ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın:  
  
    1. **Başlat** menüsünden `Control Panel`, **Yönetim Araçları**ve ardından **Bileşen Hizmetleri**' ne gidin.  
  
    2. **Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.  
  
    3. **MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.  
  
    4. **Ağ DTC erişimini** denetleyin ve **giden erişime izin verin**.  
  
    5. **Tamam**' a tıklayın ve ardından **Evet** ' e tıklayarak MSDTC hizmetini yeniden başlatın.  
  
    6. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
