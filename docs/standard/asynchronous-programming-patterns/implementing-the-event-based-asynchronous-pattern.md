---
title: Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
description: .NET ' te olay tabanlı zaman uyumsuz model (EAP) uygulamayı nasıl uygulayacağınızı öğrenin. EAP, zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standart bir yoldur.
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
ms.openlocfilehash: 466a0dd8a827cd869894106a0901bdab89601e25
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559102"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Deseni Uygulama

Fark edilebilir gecikme olabilecek bazı işlemlerle bir sınıf yazıyorsanız, [olay tabanlı zaman uyumsuz model](event-based-asynchronous-pattern-overview.md)uygulayarak bu zaman uyumsuz işlevselliği vermeyi düşünün.

Olay tabanlı zaman uyumsuz model, zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standartlaştırılmış bir yol sağlar. Gibi yardımcı sınıflarla uygulanmışsa <xref:System.ComponentModel.AsyncOperationManager> , sınıfınız ASP.net, konsol uygulamaları ve Windows Forms uygulamalar dahil olmak üzere herhangi bir uygulama modelinde doğru şekilde çalışır.

Olay tabanlı zaman uyumsuz model uygulayan bir örnek için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz kalıbı destekleyen bir bileşen uygulama](component-that-supports-the-event-based-asynchronous-pattern.md).

Basit zaman uyumsuz işlemler için <xref:System.ComponentModel.BackgroundWorker> uygun bileşeni bulabilirsiniz. Hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> bkz. [nasıl yapılır: arka planda işlem çalıştırma](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background).

Aşağıdaki listede, bu konuda açıklanan olay tabanlı zaman uyumsuz düzenin özellikleri açıklanmaktadır.

- Olay tabanlı zaman uyumsuz model uygulama olanakları

- Zaman uyumsuz yöntemleri adlandırma

- İsteğe bağlı olarak Iptali destekler

- İsteğe bağlı olarak IsBusy özelliğini destekler

- İsteğe bağlı olarak Ilerleme raporlaması için destek sağlama

- İsteğe bağlı olarak artımlı sonuçlar döndürme desteği sağlar

- Metotlarda çıkış ve başvuru parametrelerini işleme

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz model uygulama olanakları

Şu durumlarda olay tabanlı zaman uyumsuz model uygulamayı düşünün:

- Sınıfınızın istemcilerine <xref:System.Threading.WaitHandle> ve <xref:System.IAsyncResult> zaman uyumsuz işlemler için kullanılabilen nesnelere gerek yoktur, bu, yoklamanın ve <xref:System.Threading.WaitHandle.WaitAll%2A> veya istemcinin oluşturulması gereken anlamına gelir <xref:System.Threading.WaitHandle.WaitAny%2A> .

- Zaman uyumsuz işlemlerin istemci tarafından tanıdık olay/temsilci modeliyle yönetilmesini istiyorsunuz.

Herhangi bir işlem, zaman uyumsuz bir uygulama için adaydır, ancak uzun gecikme sürelerine yol açmaya beklediğinizi göz önünde bulundurmanız gerekir. Özellikle uygun olan istemciler, daha fazla müdahale gerekmeden, istemcilerin bir yöntemi çağırması ve tamamlanmasıyla ilgili bilgilendirilir işlemlerdir. Ayrıca, sürekli olarak çalışan, ilerleme durumunu, artımlı sonuçları veya durum değişikliklerini düzenli olarak bildiren işlemlerdir.

Olay tabanlı zaman uyumsuz deseninin ne zaman desteklenmeyeceğine karar verme hakkında daha fazla bilgi için, bkz. [olay tabanlı zaman uyumsuz düzenin ne zaman uygulanacağını seçme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).

## <a name="naming-asynchronous-methods"></a>Zaman uyumsuz yöntemleri adlandırma

Zaman uyumsuz bir karşılığı sağlamak istediğiniz her zaman uyumlu yöntemin *MethodName* için:

Şunu içeren bir _MethodName_**zaman uyumsuz** yöntemi tanımlayın:

- `void` döndürür.

- *MethodName* yöntemiyle aynı parametreleri alır.

- Birden çok çağırmaları kabul eder.

İsteğe bağlı olarak, _MethodName_**Async**ile özdeş, ancak başka bir nesne değerli parametresi adlı bir _MethodName_**zaman uyumsuz** aşırı yüklemesi tanımlayın `userState` . Yönteminizin birden çok eş zamanlı çağırma yönetimini yönetmeye hazırlandıysanız bunu yapın. Bu durumda `userState` değer, yöntemin etkinleştirmeleri ayırt edilebilmesi için tüm olay işleyicilerine geri gönderilir. Bunu, daha sonra alımı için Kullanıcı durumunu depolamak üzere bir yerde yapmayı da tercih edebilirsiniz.

Her ayrı _MethodName_**zaman uyumsuz** Yöntem imzası için:

1. Aşağıdaki olayı, yöntemiyle aynı sınıfta tanımlayın:

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. Aşağıdaki temsilciyi ve tanımlayın <xref:System.ComponentModel.AsyncCompletedEventArgs> . Bunlar muhtemelen sınıfın kendisi dışında, ancak aynı ad alanında tanımlanacaktır.

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

    - Alan veri bağlamayı engellediği için, _MethodName_**CompletedEventArgs** sınıfının üyelerini salt okuma özellikleri olarak gösterdiğinden emin olun.

    - <xref:System.ComponentModel.AsyncCompletedEventArgs>Sonuç üretmeyen yöntemler için herhangi bir türetilmiş sınıf tanımlamayın. Yalnızca kendi örneğini kullanmanız yeterlidir <xref:System.ComponentModel.AsyncCompletedEventArgs> .

      > [!NOTE]
      > Uygun olduğunda, temsilci ve türleri yeniden kullanmak için uygun olduğunda kusursuz kabul edilebilir <xref:System.ComponentModel.AsyncCompletedEventArgs> . Bu durumda, belirtilen bir temsilciden ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlanmayacaksa, adlandırma yöntem adı ile tutarlı olmayacaktır.

## <a name="optionally-support-cancellation"></a>İsteğe bağlı olarak Iptali destekler

Sınıfınız zaman uyumsuz işlemleri iptal etmeyi destekleyecektir, iptal etme işlemi istemciye aşağıda açıklandığı gibi gösterilmelidir. İptal desteğini tanımlamadan önce erişilmesi gereken iki karar noktası olduğunu unutmayın:

- Sınıfınızın daha sonra bu işleme eklemeleri de dahil olmak üzere, yalnızca iptali destekleyen bir zaman uyumsuz işlem var mı?

- İptali destekleyen zaman uyumsuz işlemler birden çok bekleyen işlemi destekliyor mu? Yani, _MethodName_**zaman uyumsuz** yöntemi bir `userState` parametre alır ve herhangi birinin bitmesini beklemeden birden çok yüklemeye izin veriyor mu?

İptal yönteminiz için imzanın ne olduğunu belirlemek için aşağıdaki tabloda bu iki soruya verilen yanıtları kullanın.

### <a name="visual-basic"></a>Visual Basic

||Birden çok eşzamanlı Işlem destekleniyor|Tek seferde yalnızca bir Işlem|
|------|------------------------------------------------|----------------------------------|
|Sınıfın tamamında bir zaman uyumsuz Işlem|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|Sınıfta birden çok zaman uyumsuz Işlem|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a>C\#

||Birden çok eşzamanlı Işlem destekleniyor|Tek seferde yalnızca bir Işlem|
|------|------------------------------------------------|----------------------------------|
|Sınıfın tamamında bir zaman uyumsuz Işlem|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|Sınıfta birden çok zaman uyumsuz Işlem|`void CancelAsync(object userState);`|`void CancelAsync();`|

`CancelAsync(object userState)`Yöntemini tanımlarsanız istemciler, tek bir zaman uyumsuz yöntemin yalnızca tüm etkinleştirmeleri arasında değil, nesne üzerinde çağrılan tüm zaman uyumsuz yöntemler arasında ayrım yapabilmeleri için durum değerlerini seçerken dikkatli olmalıdır.

Tek zaman uyumsuz-işlem sürümü _MethodName_**asynccancel** olarak adlandırma kararı, yöntemi Visual Studio 'nun IntelliSense gibi bir tasarım ortamında daha kolay bir şekilde keşfetmenizi temel alır. Bu, ilgili üyeleri gruplandırır ve bunları zaman uyumsuz işlevlerle hiçbir şey olmayan diğer üyelerden ayırır. Sonraki sürümlere eklenmiş ek zaman uyumsuz işlemler olabileceğini düşünüyorsanız, tanımlanması daha iyidir `CancelAsync` .

Aynı sınıfta yukarıdaki tabloda birden çok yöntem tanımlamayın. Bu anlamlı olmayacak veya bir dizi yöntem ile sınıf arabirimini yığacak hale getirir.

Bu yöntemler genellikle hemen döndürülür ve işlem gerçekten iptal edebilir veya olmayabilir. _MethodName_**tamamlandı** olayının olay işleyicisinde, _MethodName_**CompletedEventArgs** nesnesi, `Cancelled` istemcilerin İptalin oluşup oluşmadığını belirlemede kullanabileceği bir alan içerir.

[Olay tabanlı zaman uyumsuz model uygulamak Için En Iyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)bölümünde açıklanan iptal semantiğine göre ABIDE.

## <a name="optionally-support-the-isbusy-property"></a>İsteğe bağlı olarak IsBusy özelliğini destekler

Sınıfınız birden çok eş zamanlı çağırma desteklemiyorsa, bir özellik kullanıma sunulmasını düşünün `IsBusy` . Bu, bir _MethodName_zaman**uyumsuz** yönteminin _MethodName_**zaman** uyumsuz yönteminden bir özel durum yakalanmadan çalışıp çalışmadığını belirlemesine olanak sağlar.

`IsBusy` [Olay tabanlı zaman uyumsuz model uygulamak Için en iyi uygulamalar](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)bölümünde açıklanan semantiğe göre ABIDE.

## <a name="optionally-provide-support-for-progress-reporting"></a>İsteğe bağlı olarak Ilerleme raporlaması için destek sağlama

Zaman uyumsuz bir işlemin işlem sırasında ilerleme durumunu raporlamak için sık tercih edilir. Olay tabanlı zaman uyumsuz model bu işlemi gerçekleştirmek için bir kılavuz sağlar.

- İsteğe bağlı olarak, zaman uyumsuz işlem tarafından oluşturulacak ve uygun iş parçacığında çağrılan bir olayı tanımlar. <xref:System.ComponentModel.ProgressChangedEventArgs>Nesne, 0 ile 100 arasında olması beklenen bir tamsayı değerli ilerleme göstergesi taşır.

- Bu olayı aşağıdaki şekilde adlandırın:

  - `ProgressChanged` sınıfta birden çok zaman uyumsuz işlem varsa (veya gelecekteki sürümlerde birden çok zaman uyumsuz işlem içermesi için büyüme bekleniyorsa);

  - _MethodName_**ProgressChanged & lt** sınıfında tek bir zaman uyumsuz işlem varsa MethodName.

  Bu adlandırma seçeneği, Isteğe bağlı destek Iptali bölümünde açıklandığı gibi, iptal yöntemi için oluşturulan paraleller.

Bu olay, <xref:System.ComponentModel.ProgressChangedEventHandler> temsilci imzasını ve <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfını kullanmalıdır. Alternatif olarak, daha fazla alana özgü bir ilerleme göstergesi sağlandıysa (örneğin, okunan bayt sayısı ve bir indirme işlemi için toplam bayt), türetilmiş bir sınıfı tanımlamanız gerekir <xref:System.ComponentModel.ProgressChangedEventArgs> .

`ProgressChanged`Desteklediği zaman uyumsuz yöntemlerin sayısından bağımsız olarak, sınıfı için yalnızca bir veya _MethodName_**ProgressChanged & lt** olayı olduğunu unutmayın. İstemcilerin, `userState` birden çok eşzamanlı işlemde ilerleme güncelleştirmelerini ayırt etmek Için _MethodName_**zaman uyumsuz** yöntemlerine geçirilen nesneyi kullanması beklenir.

Birden çok işlemin ilerleme durumunu desteklediği ve her biri ilerleme için farklı bir gösterge döndüren durumlar olabilir. Bu durumda, tek bir `ProgressChanged` olay uygun değildir ve birden çok olayı desteklemeyi düşünebilirsiniz `ProgressChanged` . Bu durumda, her _MethodName_**zaman uyumsuz** yöntemi için _MethodName_**ProgressChanged & lt** 'in bir adlandırma modelini kullanır.

İlerleme durumuna göre ABIDE [olay tabanlı zaman uyumsuz model uygulamak Için En Iyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)açıklanmıştır.

## <a name="optionally-provide-support-for-returning-incremental-results"></a>İsteğe bağlı olarak artımlı sonuçlar döndürme desteği sağlar

Bazen zaman uyumsuz bir işlem, tamamlanmadan önce artımlı sonuçlar döndürebilir. Bu senaryoyu desteklemek için kullanılabilecek birçok seçenek vardır. Bazı örnekler aşağıda verilmiştir.

### <a name="single-operation-class"></a>Tek işlem sınıfı

Sınıfınız yalnızca tek bir zaman uyumsuz işlemi destekliyorsa ve bu işlem artımlı sonuçlar döndürebiliyor, sonra:

- <xref:System.ComponentModel.ProgressChangedEventArgs>Türü artımlı sonuç verilerini taşımak için genişletin ve bu genişletilmiş verilerle bir _MethodName_**ProgressChanged & lt** olayı tanımlayın.

- Raporlamak için artımlı bir sonuç olduğunda bu _MethodName_**ProgressChanged & lt** olayını yükseltin.

Bu çözüm, özel olarak tek bir zaman uyumsuz-Operation sınıfına uygulanır çünkü "All Operations" üzerinde artımlı sonuçlar döndürmek için bir sorun yoktur, çünkü _MethodName_**ProgressChanged & lt** olayı.

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Homojen artımlı sonuçları olan birden çok işlem sınıfı

Bu durumda, sınıfınız birden çok zaman uyumsuz yöntemi destekler, her biri artımlı sonuçları döndürmüştür ve bu artımlı sonuçların hepsi aynı türde verilere sahiptir.

Aynı <xref:System.EventArgs> yapı tüm artımlı sonuçlar için çalışacaktır, tek işlem sınıfları için yukarıda açıklanan modeli izleyin. `ProgressChanged`Birden çok zaman uyumsuz yöntem için geçerli olduğundan _MethodName_**ProgressChanged & lt** olayı yerine bir olay tanımlayın.

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Heterojen artımlı sonuçlarla çoklu işlem sınıfı

Sınıfınız, her biri farklı türde veriler döndüren birden çok zaman uyumsuz yöntemi destekliyorsa şunları yapmalısınız:

- Artımlı sonuç raporlarınızı ilerleme raporınızdan ayırın.

- _MethodName_**ProgressChanged** <xref:System.EventArgs> Bu yöntemin artımlı sonuç verilerini işlemek için her zaman uyumsuz yöntem Için uygun olan ayrı bir MethodName ProgressChanged & lt olayı tanımlayın.

[Olay tabanlı zaman uyumsuz model uygulamak Için En Iyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)bölümünde açıklandığı gibi ilgili iş parçacığında bu olay işleyicisini çağırın.

## <a name="handling-out-and-ref-parameters-in-methods"></a>Metotlarda çıkış ve başvuru parametrelerini işleme

Ve ' nin kullanımı, genel olarak, .NET Framework önerilse de `out` `ref` , mevcut olduklarında izlenecek kurallar aşağıda verilmiştir:

Zaman uyumlu bir yöntem *MethodName*:

- `out`*MethodName* parametresi _MethodName_**Async**öğesinin bir parçası olmamalıdır. Bunun yerine _, MethodName parametresinin bir parçası_olmaları *gerekir (daha* uygun bir ad olmadıkça) parametre eşdeğeri olarak aynı**ada sahip.**

- `ref`*MethodName* parametresi, _MethodName_**zaman uyumsuz**değerinin bir parçası olarak ve *MethodName (daha* uygun bir ad olmadıkça) parametresi ile aynı ada sahip _MethodName_**CompletedEventArgs** öğesinin bir parçası olarak görünmelidir.

Örneğin, verilen:

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

Zaman uyumsuz yönteminiz ve <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı şu şekilde görünür:

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
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)
- [Nasıl yapılır: Arka Planda İşlem Çalıştırma](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](/dotnet/desktop/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation)
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
