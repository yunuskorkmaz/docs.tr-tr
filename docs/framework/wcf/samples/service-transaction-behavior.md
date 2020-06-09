---
title: Hizmet İşlem Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 0be5bf0dbe6416febb898fb5150c5a516c8b0969
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591533"
---
# <a name="service-transaction-behavior"></a>Hizmet İşlem Davranışı

Bu örnek, hizmet işlem davranışını denetlemek için istemci ile eşgüdümlü bir işlemin ve ServiceBehaviorAttribute ve OperationBehaviorAttribute ayarlarının kullanımını gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır, ancak bir veritabanı tablosunda gerçekleştirilen işlemlerin sunucu günlüğünü ve Hesaplayıcı işlemleri için durum bilgisi olan bir çalışan toplamı korumak üzere genişletilir. Sunucu günlüğü tablosuna kalıcı yazma işlemleri, istemci ile eşgüdümlü bir işlemin sonucuna bağımlıdır. istemci işlemi tamamlanmazsa, Web hizmeti işlemi veritabanı güncelleştirmelerinin yürütülmemesini sağlar.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Hizmetin sözleşmesi, tüm işlemlerin isteklerle birlikte akışını gerektirdiğini tanımlar:

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

Gelen işlem akışını etkinleştirmek için hizmet, transactionFlow özniteliği olarak ayarlanmış sistem tarafından sağlanmış wsHttpBinding ile yapılandırılır `true` . Bu bağlama, birlikte çalışabilen WSAtomicTransactionOctober2004 protokolünü kullanır:

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

Hem hizmet hem de bir işlem bağlantısı başlattıktan sonra istemci, bu işlemin kapsamındaki çeşitli hizmet işlemlerine erişir ve sonra işlemi tamamlar ve bağlantıyı kapatır:

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

Hizmette, hizmet işlem davranışını etkileyen üç öznitelik vardır ve bunu aşağıdaki yollarla yapabilirler:

- Üzerinde `ServiceBehaviorAttribute` :

  - `TransactionTimeout`Özelliği, bir işlemin tamamlaması gereken zaman dilimini belirtir. Bu örnekte, 30 saniyeye ayarlanır.

  - `TransactionIsolationLevel`Özelliği, hizmetin desteklediği yalıtım düzeyini belirtir. İstemcinin yalıtım düzeyini eşleştirmek için bu gereklidir.

  - `ReleaseServiceInstanceOnTransactionComplete`Özelliği, bir işlem tamamlandığında hizmet örneğinin geri dönüştürülüp dönüştürülmeyeceğini belirtir. Hizmet, olarak ayarlanarak `false` , işlem istekleri genelinde aynı hizmet örneğini tutar. Bu, toplam çalışma sağlamak için gereklidir. Olarak ayarlanırsa `true` , tamamlanan her eylemden sonra yeni bir örnek oluşturulur.

  - `TransactionAutoCompleteOnSessionClose`Özelliği, oturum kapandığında bekleyen işlemlerin tamamlanıp tamamlanmadığını belirtir. `false`' I ' a ayarlayarak, tek tek işlemler, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> özelliği, `true` işlemleri tamamlamaya yönelik bir yönteme çağrı yapmak ya da açıkça gerektirmek için gerekir <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> . Bu örnekte her iki yaklaşım da gösterilmektedir.

- Üzerinde `ServiceContractAttribute` :

  - `SessionMode`Özelliği, hizmetin uygun istekleri mantıksal bir oturumla karşılıklı olarak içerip içermediğini belirtir. Bu hizmet, OperationBehaviorAttribute TransactionAutoComplete özelliğinin `false` (çarp ve Böl) olarak ayarlandığı işlemleri içerdiğinden, `SessionMode.Required` belirtilmesi gerekir. Örneğin, çarpma işlemi, işlemini tamamlamaz ve bunun yerine yöntemi kullanılarak tamamlamaya bölmek için daha sonraki bir çağrıya bağımlıdır `SetTransactionComplete` ; hizmet, bu işlemlerin aynı oturum içinde gerçekleştiğini belirleyebilmelidir.

- Üzerinde `OperationBehaviorAttribute` :

  - `TransactionScopeRequired`Özelliği işlemin işlemlerinin bir işlem kapsamı içinde yürütülüp yürütülmeyeceğini belirtir. Bu, `true` Bu örnekteki tüm işlemler için olarak ayarlanır ve istemci, işlemini tüm işlemlere akdığı için, bu istemci işleminin kapsamında eylemler oluşur.

  - `TransactionAutoComplete`Özelliği, işlenmeyen özel durumlar oluşursa yöntemin yürütme işleminin otomatik olarak tamamlanıp tamamlanmadığını belirtir. Daha önce açıklandığı gibi, bu, `true` Ekle ve çıkart işlemleri için, `false` çarpma ve bölme işlemleri için olarak ayarlanır. Ekleme ve çıkarma işlemleri, eylemlerini otomatik olarak tamamlar, bölme kendi eylemlerini yöntemine açık bir çağrı aracılığıyla tamamlar `SetTransactionComplete` ve çarpma işlemleri eylemlerini tamamlamaz ve bunun yerine, eylemleri tamamlamaya yönelik daha sonraki bir çağrı gerektirir.

Öznitelikli hizmet uygulamasını aşağıdaki gibidir:

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

    // Logging method omitted for brevity
}
```

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

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

Hizmet işlemi isteklerinin günlüğe kaydedilmesi, hizmetin konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

Hesaplamaların toplam çalışma sayısını tutmanın yanı sıra hizmetin örneklerin oluşturulmasını (Bu örnek için bir örnek) raporluyor ve işlem isteklerinin bir veritabanına günlüğe kaydettiği unutulmamalıdır. Tüm istekler istemcinin işlemini Flow için, bu işlemi tamamlamamaya yönelik herhangi bir hata, tüm veritabanı işlemlerinin geri alınmasına neden olur. Bu, çeşitli yollarla gösterilmiştir:

- İstemcinin `tx.Complete` () çağrısı yapın ve yeniden çalıştırın. Bu, istemcinin işlemini tamamlamadan işlem kapsamından çıkılıyor.

- Ayırma hizmeti işlemine çağrı yap-bu sonuçlar, çarpma işlemi tarafından başlatılan eylemin tamamlanmasını önler ve bu nedenle istemcinin işleminin sonunda da tamamlanamamasına neden olur.

- İstemcinin işlem kapsamında herhangi bir yerde işlenmeyen bir özel durum oluşturur. bu benzer şekilde istemcinin işlemini tamamlamasını önler.

Bunlardan herhangi birinin sonucu, bu kapsamda gerçekleştirilen işlemlerin hiçbirinin yürütülmediği ve veritabanında kalıcı olan satırların sayısının artmadığı bir sonucudur.

> [!NOTE]
> Yapı işleminin bir parçası olarak veritabanı dosyası bin klasörüne kopyalanır. Visual Studio projesinde yer alan dosya yerine günlüğe kalıcı olan satırları gözlemlemek için veritabanı dosyasının bu kopyasına bakmanız gerekir.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. SQL Server 2005 Express Sürüm veya SQL Server 2005 ' i yüklediğinizden emin olun. Hizmetin App. config dosyasında, veritabanı `connectionString` ayarlanabilir veya appSettings değeri olarak ayarlanarak veritabanı etkileşimleri devre dışı bırakılabilir `usingSql` `false` .

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

Örneği makinelerde çalıştırırsanız, ağ işlem akışını etkinleştirmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırmanız ve Windows Communication Foundation (WCF) işlemleri ağ desteğini etkinleştirmek için WsatConfig. exe aracını kullanmanız gerekir.

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) hizmetini makineler genelinde çalıştırmayı destekleyecek şekilde yapılandırmak için

1. Hizmet makinesinde, gelen ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın.

    1. **Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.

    2. **Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.

    3. **MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.

    4. **Ağ DTC erişimini** denetleyin ve **gelen erişime izin verin**.

    5. MS DTC hizmetini yeniden başlatmak için **Evet** ' e tıklayın ve ardından **Tamam**' a tıklayın.

    6. **Tamam**’a tıklayarak iletişim kutusunu kapatın.

2. Hizmet makinesi ve istemci makinesinde, Windows Güvenlik Duvarı 'nı, hariç tutulan uygulamalar listesine Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) içerecek şekilde yapılandırın:

    1. Windows Güvenlik Duvarı uygulamasını Denetim Masası 'ndan çalıştırın.

    2. **Özel durumlar** sekmesinde **Program Ekle**' ye tıklayın.

    3. C:\WINDOWS\System32. klasörüne gidin

    4. MSDTC. exe ' yi seçin ve **Aç**' a tıklayın.

    5. **Tamam** ' a tıklayarak **Program Ekle** iletişim kutusunu kapatın ve yeniden **Tamam** ' a tıklayarak Windows Güvenlik Duvarı uygulamasını kapatın.

3. İstemci makinesinde, giden ağ işlemlerine izin vermek için MSDTC 'yi yapılandırın:

    1. **Başlat** menüsünde, **Denetim Masası**' na, ardından **Yönetimsel Araçlar**' a ve ardından **Bileşen Hizmetleri**' ne gidin.

    2. **Bilgisayarım ' a** sağ tıklayın ve **Özellikler**' i seçin.

    3. **MSDTC** sekmesinde **Güvenlik Yapılandırması**' na tıklayın.

    4. **Ağ DTC erişimini** denetleyin ve **giden erişime izin verin**.

    5. MS DTC hizmetini yeniden başlatmak için **Evet** ' e tıklayın ve ardından **Tamam**' a tıklayın.

    6. **Tamam**’a tıklayarak iletişim kutusunu kapatın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
