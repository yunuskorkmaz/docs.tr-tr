---
title: Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663703"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Deseni Uygulama

Fark edilebilir gecikmelere neden olabilecek bazı işlemlere sahip bir sınıf yazıyorsanız, Olay tabanlı Eşzamanlı [Desen Genel Bakış'ı](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)uygulayarak sınıfa eşzamanlı işlevsellik vermeyi düşünün.

Olay tabanlı Asynchronous Pattern, eşzamanlı özelliklere sahip bir sınıfı paketlemek için standartlaştırılmış bir yol sağlar. Gibi yardımcı sınıflarla <xref:System.ComponentModel.AsyncOperationManager>uygulanırsa, ASP.NET, Konsol uygulamaları ve Windows Forms uygulamaları da dahil olmak üzere herhangi bir uygulama modeli altında sınıfınız doğru şekilde çalışır.

Olay tabanlı Asynchronous Deseni'ni uygulayan bir örnek için [bkz.](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)

Basit asynchronous işlemleri için <xref:System.ComponentModel.BackgroundWorker> bileşeni uygun bulabilirsiniz. Hakkında <xref:System.ComponentModel.BackgroundWorker>daha fazla bilgi için [bkz: Arka Planda Bir İşlem çalıştırın.](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)

Aşağıdaki listede, bu konuda tartışılan Olay tabanlı Eşzamanlı Desen'in özellikleri açıklanmaktadır.

- Olay Tabanlı Asynchronous Modelini Uygulama Fırsatları

- Adsız Yöntemler adlandırma

- İsteğe Bağlı Destek İptali

- İsteğe Bağlı Olarak IsBusy Özelliğini Destekleyin

- İsteğe Bağlı Olarak İlerleme Raporlaması için Destek Sağlayın

- İsteğe Bağlı Olarak Artan Sonuçları Döndürmek Için Destek Sağlayın

- Yöntemlerde Çıkış ve Ref Parametrelerinin İşlemi

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Asynchronous Modelini Uygulama Fırsatları

Aşağıdaki halde Event tabanlı Eşzamanlı Desen'i uygulamayı düşünün:

- Sınıfınızın istemcileri gerekmez <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> ve nesneleri eşzamanlı işlemler için kullanılabilir, yani <xref:System.Threading.WaitHandle.WaitAll%2A> yoklama ve veya <xref:System.Threading.WaitHandle.WaitAny%2A> istemci tarafından inşa edilmesi gerekir.

- Eşzamanlı işlemlerin tanıdık olay/temsilci modeliyle istemci tarafından yönetilmesini istiyorsunuz.

Herhangi bir işlem eşzamanlı bir uygulama için bir adaydır, ancak uzun gecikmelere maruz kalmak için beklediğiniz olanlar dikkate alınmalıdır. Özellikle uygun olan, müşterilerin bir metodu aradığı ve tamamlandığında bilgilendirildiği ve başka bir müdahale gerektirmeden bilgilendirildiği işlemlerdir. Ayrıca, sürekli çalışan, düzenli olarak ilerleme, artımlı sonuçlar veya durum değişiklikleri istemcileri bildiren işlemlerdir.

Olay tabanlı Eşzamanlı Deseni'ni ne zaman destekleyeceğine karar verme hakkında daha fazla bilgi için olay tabanlı Eşzamanlı [Deseni'nin ne zaman uygulanacağına karar](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)verme konusuna bakın.

## <a name="naming-asynchronous-methods"></a>Adsız Yöntemler adlandırma

Asynchronous muadili sağlamak istediğiniz her senkron yöntem *MethodName* için:

Bir _MethodName_**Async** yöntemi tanımlayın:

- `void` döndürür.

- *MethodName* yöntemiyle aynı parametreleri alır.

- Birden çok çağrı kabul eder.

İsteğe bağlı olarak, MethodName**Async**ile aynı olan, ancak nesne değeri olan `userState`ek bir parametre adı verilen bir _MethodName_ _MethodName_**Async** aşırı yükünü tanımlayın. Yönteminizin birden çok eşzamanlı çağrılarını yönetmeye hazırsanız bunu yapın, `userState` bu durumda değer yöntemin çağrılarını ayırt etmek için tüm olay işleyicilerine geri teslim edilir. Ayrıca, bunu yalnızca daha sonra alma için kullanıcı durumunu depolamak için bir yer olarak yapmayı seçebilirsiniz.

Her ayrı _MethodName_**Async** yöntemi imzası için:

1. Yöntemle aynı sınıfta aşağıdaki olayı tanımlayın:

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. Aşağıdaki temsilciyi <xref:System.ComponentModel.AsyncCompletedEventArgs>tanımlayın ve . Bunlar büyük olasılıkla sınıfın kendisi dışında, ancak aynı ad alanında tanımlanır.

    ```vb
    Public Delegate Sub MethodNameCompletedEventHandler( _
        ByVal sender As Object, _
        ByVal e As MethodNameCompletedEventArgs)

    Public Class MethodNameCompletedEventArgs
        Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As MyReturnType
    End Property
    ```

    ```csharp
    public delegate void MethodNameCompletedEventHandler(object sender,
        MethodNameCompletedEventArgs e);

    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
    {
        public MyReturnType Result { get; }
    }
    ```

    - _MethodName_**CompletedEventArgs** sınıfının, alanlar veri bağlamayı önlediği için, üyelerini alan olarak değil, salt okunur özellikler olarak ortaya çıkardığından emin olun.

    - Sonuç üretmeyen <xref:System.ComponentModel.AsyncCompletedEventArgs>yöntemler için türetilmiş sınıfları tanımlamayın. Sadece kendi bir <xref:System.ComponentModel.AsyncCompletedEventArgs> örneğini kullanın.

      > [!NOTE]
      > Temsilci ve <xref:System.ComponentModel.AsyncCompletedEventArgs> türleri yeniden kullanmak mümkün ve uygun olduğunda son derece kabul edilebilir. Bu durumda, belirli bir temsilci ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlı olmayacaktır, çünkü adlandırma yöntem adı ile tutarlı olmayacaktır.

## <a name="optionally-support-cancellation"></a>İsteğe Bağlı Destek İptali

Sınıfınız eşzamanlı işlemleri iptal etmeyi destekleyecekse, iptal işlemi aşağıda açıklandığı gibi istemciye açıklanmalıdır. İptal desteğinizi tanımlamadan önce ulaşılması gereken iki karar noktası olduğunu unutmayın:

- Sınıfınızın, gelecekte beklenen eklemeler de dahil olmak üzere, iptali destekleyen tek bir eşzamanlı işlemi var mı?

- İptali destekleyen eşzamanlı işlemler birden çok bekleyen işlemi destekleyebilir mi? Diğer bir deyişle, _MethodName_**Async** yöntemi bir parametre alır ve herhangi bir `userState` bitirmek için beklemeden önce birden çok çağrıizin verir?

İptal yönteminiziçin imzanın ne olması gerektiğini belirlemek için aşağıdaki tablodaki bu iki sorunun yanıtlarını kullanın.

### <a name="visual-basic"></a>Visual Basic

||Birden Fazla Eşzamanlı Operasyon Desteklendi|Aynı Anda Yalnızca Bir İşlem|
|------|------------------------------------------------|----------------------------------|
|Tüm sınıfta bir Async İşlemi|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|Sınıfta Birden Çok Async İşlemleri|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a>C\#

||Birden Fazla Eşzamanlı Operasyon Desteklendi|Aynı Anda Yalnızca Bir İşlem|
|------|------------------------------------------------|----------------------------------|
|Tüm sınıfta bir Async İşlemi|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|Sınıfta Birden Çok Async İşlemleri|`void CancelAsync(object userState);`|`void CancelAsync();`|

`CancelAsync(object userState)` Yöntemi tanımlarsanız, istemciler, yalnızca tek bir eşzamanlı yöntemin tüm çağrıları arasında değil, nesne üzerinde çağrılan tüm eşzamanlı yöntemler arasında ayırt yeteneğine sahip yapmak için durum değerlerini seçerken dikkatli olmalıdır.

Tek async-operation sürümü _MethodName_**AsyncCancel** adlandırma kararı daha kolay Visual Studio's IntelliSense gibi bir tasarım ortamında yöntemi keşfetmek mümkün dayanmaktadır. Bu, ilgili üyeleri gruplar ve onları eşzamanlı işlevsellikle ilgisi olmayan diğer üyelerden ayırır. Sonraki sürümlerde ek eşzamanlı işlemler ekleyebileceğini bekliyorsanız, tanımlamak `CancelAsync`daha iyidir.

Aynı sınıfta yukarıdaki tablodan birden fazla yöntem tanımlamayın. Bu mantıklı olmayacaktır, ya da yöntemlerin çoğalması ile sınıf arayüzü darmadağın olacaktır.

Bu yöntemler genellikle hemen geri döner ve işlem gerçekten iptal edebilir veya olmayabilir. _MethodName_**Completed** olayının olay işleyicisinde, _MethodName_**CompletedEventArgs** nesnesi, istemcilerin iptalin gerçekleşip gerçekleşmediğini belirlemek için kullanabileceği bir `Cancelled` alan içerir.

[Olay tabanlı Asynchronous Desen Uygulamak için En İyi Uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanan iptal semantik uymak.

## <a name="optionally-support-the-isbusy-property"></a>İsteğe Bağlı Olarak IsBusy Özelliğini Destekleyin

Sınıfınız birden çok eşzamanlı çağrıyı desteklemiyorsa, `IsBusy` bir özelliği açığa çıkarmayı düşünün. Bu, geliştiricilerin _MethodName_**Async** yönteminden bir özel durum yakalamadan bir _MethodName_**Async** yönteminin çalışıp çalışmadığını belirlemesine olanak tanır.

Olay tabanlı `IsBusy` [Asynchronous Desen Uygulamak için En İyi Uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanan semantik tarafından abide.

## <a name="optionally-provide-support-for-progress-reporting"></a>İsteğe Bağlı Olarak İlerleme Raporlaması için Destek Sağlayın

Eşzamanlı bir işlemin çalışması sırasında ilerlemeyi bildirmesi sık sık istenir. Olay tabanlı Asynchronous Pattern bunu yapmak için bir kılavuz sağlar.

- İsteğe bağlı olarak, eşzamanlı işlem tarafından yükseltilecek ve uygun iş parçacığıüzerinde çağrılacak bir olay tanımlayın. Nesne, <xref:System.ComponentModel.ProgressChangedEventArgs> 0 ile 100 arasında olması beklenen bir veyasede değerli ilerleme göstergesi taşır.

- Bu olayı aşağıdaki gibi adlandırın:

  - `ProgressChanged`sınıfın birden çok eşzamanlı işlemi varsa (veya gelecekteki sürümlerde birden çok eşzamanlı işlem içerecek şekilde büyümesi bekleniyorsa);

  - _MethodName_ProgressSınıfın tek bir eşzamanlı işlemi varsa**değiştirildi.**

  Bu adlandırma seçimi, İsteğe Bağlı Destek İptali bölümünde açıklandığı gibi, iptal yöntemi için yapılan larla paraleldir.

Bu olay temsilci <xref:System.ComponentModel.ProgressChangedEventHandler> imzasını <xref:System.ComponentModel.ProgressChangedEventArgs> ve sınıfı kullanmalıdır. Alternatif olarak, daha fazla etki alanına özgü ilerleme göstergesi sağlanabilirse (örneğin, bir indirme işlemi için bayt okuma <xref:System.ComponentModel.ProgressChangedEventArgs>ve toplam bayt), türetilmiş bir sınıf tanımlamalısınız.

Desteklediği eşzamanlı yöntem `ProgressChanged` sayısına bakılmaksızın, sınıf için yalnızca bir veya _MethodName_**ProgressChanged** olayı olduğunu unutmayın. İstemcilerin, `userState` birden çok eşzamanlı işlemdeki ilerleme güncelleştirmelerini ayırt etmek için _MethodName_**Async** yöntemlerine geçirilen nesneyi kullanması beklenir.

Birden çok operasyonun ilerlemeyi desteklediği ve her birinin ilerleme için farklı bir gösterge döndürdettiği durumlar olabilir. Bu durumda, tek `ProgressChanged` bir olay uygun değildir ve birden `ProgressChanged` çok olayı desteklemeyi düşünebilirsiniz. Bu durumda, her _MethodName_**Async** yöntemi için _MethodName_**ProgressChanged'in** bir adlandırma deseni kullanın.

İlerleme raporlama semantik tarafından olay [tabanlı Asynchronous Desen uygulanması için En İyi Uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanan uymak.

## <a name="optionally-provide-support-for-returning-incremental-results"></a>İsteğe Bağlı Olarak Artan Sonuçları Döndürmek Için Destek Sağlayın

Bazen bir eşzamanlı işlem tamamlanmadan önce artımlı sonuçlar döndürebilir. Bu senaryoyu desteklemek için kullanılabilecek birkaç seçenek vardır. Bazı örnekler izleyin.

### <a name="single-operation-class"></a>Tek İşlemli Sınıf

Sınıfınız yalnızca tek bir eşzamanlı işlemi destekliyorsa ve bu işlem artımlı sonuçlar döndürebiliyorsa, o zaman:

- Türü artımlı sonuç verilerini taşımak için genişletin ve bu genişletilmiş verilerle bir _MethodName_**ProgressChanged** olayını tanımlayın. <xref:System.ComponentModel.ProgressChangedEventArgs>

- Rapor etmek için artımlı bir sonuç olduğunda bu _MethodName_**ProgressChanged** olayını yükseltin.

Bu çözüm, _MethodName_**ProgressChanged** olayının yaptığı gibi "tüm işlemler"de artımlı sonuçlar döndürmek için aynı olayla ilgili bir sorun olmadığından, tek eşli çalışma sınıfı için özel olarak geçerlidir.

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Homojen Artımlı Sonuçlarla Çoklu İşlem Sınıfı

Bu durumda, sınıfınız her biri artımlı sonuçlar döndürebilen birden çok eşzamanlı yöntemi destekler ve bu artımlı sonuçların tümü aynı veri türüne sahiptir.

Aynı <xref:System.EventArgs> yapı tüm artımlı sonuçlar için çalışacağından, tek işlemli sınıflar için yukarıda açıklanan modeli izleyin. Birden `ProgressChanged` çok eşzamanlı yöntem için geçerli olduğundan, _Bir YöntemAdı_**İlerlemeDeğiştirildi** olayı yerine bir olay tanımlayın.

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Heterojen Artımlı Sonuçlarla Çoklu İşlem Sınıfı

Sınıfınız, her biri farklı türde veri döndüren birden çok eşzamanlı yöntemi destekliyorsa, şunları

- Artımlı sonuç raporlamanızı ilerleme raporlamanızdan ayırın.

- Bu yöntemin artımlı sonuç <xref:System.EventArgs> verilerini işlemek için her bir eşzamanlı yöntem için uygun olan ayrı bir _MethodName_**ProgressChanged** olayı tanımlayın.

[Olay tabanlı Asynchronous Deseni'ni Uygulamak için En İyi Uygulamalar'da](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklandığı gibi, bu olay işleyicisini uygun iş parçacığına çağırın.

## <a name="handling-out-and-ref-parameters-in-methods"></a>Yöntemlerde Çıkış ve Ref Parametrelerinin İşlemi

Genel olarak `out` .NET Çerçevesi'nde kullanımı ve `ref` kullanımı önerilse de, mevcut olduklarında uyulması gereken kurallar şunlardır:

Senkron bir yöntem verilen *MethodName*:

- `out`*MethodName* parametreleri _MethodName_**Async'in**bir parçası olmamalıdır. Bunun yerine, _MethodName'deki_parametre eşdeğeri ile aynı ada sahip *MethodName* MethodName**CompletedEventArgs'ın** bir parçası olmalıdırlar (daha uygun bir ad yoksa).

- `ref`*MethodName* parametreleri _MethodName_**Async'in**bir parçası olarak ve _MethodName'deki_parametre eşdeğeri ile *MethodName* aynı ada sahip MethodName**CompletedEventArgs'ın** bir parçası olarak görünmelidir (daha uygun bir ad yoksa).

Örneğin, verilen:

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

Asynchronous yönteminiz <xref:System.ComponentModel.AsyncCompletedEventArgs> ve sınıfı şu na benzerdi:

```vb
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)

Public Class MethodNameCompletedEventArgs
    Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As Integer
    End Property
    Public ReadOnly Property Arg2() As String
    End Property
    Public ReadOnly Property Arg3() As String
    End Property
End Class
```

```csharp
public void MethodNameAsync(string arg1, string arg2);

public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
{
    public int Result { get; };
    public string Arg2 { get; };
    public string Arg3 { get; };
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
