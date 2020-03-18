---
title: İstisnalar için En İyi Uygulamalar - .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 1de231b01e3fa97e78a87ae6b0595a9b5536374e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160176"
---
# <a name="best-practices-for-exceptions"></a>Özel durumlar için en iyi uygulamalar

İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler. Bu bölümde, özel durumları işlemek ve oluşturmak için en iyi uygulamalar açıklanmaktadır.

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a>Hatalardan kurtulmak veya kaynakları serbest bırakmak için try/catch/finally bloklarını kullanma

Olası `try` / `catch` bir özel durum oluşturabilecek kodun etrafındaki blokları kullanın ***ve*** kodunuz bu özel durumdan kurtarabilir. Bloklarda, `catch` her zaman en çok türetilenden en az türetilmiş özel durumları sıralar. Tüm özel <xref:System.Exception>durumlar. Daha fazla türetilmiş özel durumlar, taban özel durum sınıfı için bir catch yan tümcesi tarafından önce gelen bir catch yan tümcesi tarafından işlenmez. Kodunuz bir özel durum kurtarılamadığınızda, bu özel durumu yakalamayın. Mümkünse kurtarmak için arama yığınının daha yukarısına yöntemleri etkinleştirin.

İfadelerle veya `finally` bloklarla `using` ayrılan kaynakları temizleyin. Özel `using` durumlar atıldığında kaynakları otomatik olarak temizlemek için deyimleri tercih edin. Uygulanmayan `finally` <xref:System.IDisposable>kaynakları temizlemek için blokları kullanın. Bir `finally` yan tümcedeki kod, özel durumlar atıldığında bile hemen hemen her zaman yürütülür.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Özel durumlar atmadan sık karşılaşılan koşulları işleme

Oluşması muhtemel ancak bir özel durum tetikleyebilecek koşullar için, bunları özel durumlardan kaçınacak şekilde işlemeyi düşünün. Örneğin, zaten kapalı olan bir bağlantıyı kapatmaya çalışırsanız, `InvalidOperationException`bir . Kapatmaya çalışmadan önce `if` bağlantı durumunu denetlemek için bir deyim kullanarak bunu önleyebilirsiniz.

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

Kapatmadan önce bağlantı durumunu denetlemezseniz, `InvalidOperationException` özel durumu yakalayabilirsiniz.

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

Seçilecek yöntem, olayın ne sıklıkta gerçekleşmesini beklediğiniz bağlıdır.

- Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın. Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.

- Olay olağan bir şekilde gerçekleşirse ve normal yürütmenin bir parçası olarak kabul edilebilirse koddaki hata koşullarını denetleyin. Sık karşılaşılan hata koşullarını denetlediğinizde, özel durumlar dan kaçınmak için daha az kod yürütülür.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Özel durumların önlenebileceği şekilde tasarım sınıfları

Bir sınıf, özel bir durum tetikleyen bir arama yapmaktan kaçınmanızı sağlayan yöntemler veya özellikler sağlayabilir. Örneğin, bir <xref:System.IO.FileStream> sınıf, dosyanın sonuna ulaşılıp ulaşılmadığını belirlemeye yardımcı olan yöntemler sağlar. Bunlar, dosyanın sonundan geçmiş okursanız atılan özel durum lardan kaçınmak için kullanılabilir. Aşağıdaki örnek, bir özel durum tetiklemeden bir dosyanın sonuna kadar nasıl okunacak larını gösterir.

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

Özel durumları önlemenin başka bir yolu da, özel durum atmak yerine son derece yaygın hata durumları için null (veya varsayılan) döndürmektir. Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir. Bu gibi durumlarda null (veya varsayılan) döndürerek, bir uygulamaya performans etkisini en aza indirirsiniz.

Değer türleri için, `Nullable<T>` hata göstergeniz olarak kullanılıp kullanılmayacağınız veya varsayılan olarak, belirli uygulamanız için göz önünde bulundurulması gereken bir şeydir. Kullanarak `Nullable<Guid>`, `default` `null` yerine `Guid.Empty`olur . Bazı zamanlar, `Nullable<T>` bir değer mevcut veya yok olduğunda ekleme daha net yapabilirsiniz. Diğer zamanlarda, `Nullable<T>` ekleme gerekli değildir denetlemek için ek durumlarda oluşturabilir ve yalnızca hata potansiyel kaynakları oluşturmak için hizmet vermektedir.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Hata kodu döndürmek yerine özel durumlar atma

Özel durumlar, arama kodu iade kodunu denetlemediğinden hataların fark edilmemesini sağlar.

## <a name="use-the-predefined-net-exception-types"></a>Önceden tanımlanmış .NET özel durum türlerini kullanma

Yalnızca önceden tanımlanmış bir sınıf geçerli olmadığında yeni bir özel durum sınıfı tanıtın. Örnek:

- Nesnenin <xref:System.InvalidOperationException> geçerli durumu göz önüne alındığında özellik kümesi veya yöntem çağrısı uygun değilse bir özel durum atın.

- Geçersiz <xref:System.ArgumentException> parametreler geçirilirse türeyen bir <xref:System.ArgumentException> özel durum veya önceden tanımlanmış sınıflardan birini atın.

## <a name="end-exception-class-names-with-the-word-exception"></a>Özel durum sınıf adlarını sözcüğüyle sonlandırır`Exception`

Özel bir özel durum gerektiğinde, uygun bir şekilde <xref:System.Exception> adlandırın ve sınıftan türetin. Örnek:

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a>Özel özel durum sınıflarına üç oluşturucu ekleme

Kendi özel durum sınıflarınızı oluştururken en az üç ortak oluşturucuyu kullanın: parametresiz oluşturucu, dize iletisi alan bir oluşturucu ve dize iletisi ve iç özel durum alan bir oluşturucu.

- <xref:System.Exception.%23ctor>, varsayılan değerleri kullanır.

- <xref:System.Exception.%23ctor%28System.String%29>, bir dize iletisi kabul eder.

- <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, bir dize iletisi ve bir iç özel durum kabul eder.

Örneğin, [bkz.](how-to-create-user-defined-exceptions.md)

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Kod uzaktan yürütüldüğünde özel durum verilerinin kullanılabilir olduğundan emin olun

Kullanıcı tanımlı özel durumlar oluşturduğunuzda, özel durumlar için meta verilerin uzaktan yürütülen kodiçin kullanılabilir olduğundan emin olun.

Örneğin, App Etki Alanlarını destekleyen .NET uygulamalarında, Uygulama etki alanlarında özel durumlar oluşabilir. App Domain A'nın, özel durum oluşturan kodu yürüten App Domain B oluşturduğunu varsayalım. App Domain A'nın özel durumu düzgün bir şekilde yakalayaması ve işlemesi için, App Domain B tarafından atılan özel durumu içeren derlemeyi bulabilmek gerekir. App Domain B, uygulama tabanı altında bir derlemede bulunan ancak App Domain A'nın uygulama tabanı altında olmayan bir özel durum oluşturursa, App <xref:System.IO.FileNotFoundException> Domain A özel durumu bulamaz ve ortak dil çalışma süresi bir özel durum oluşturur. Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:

- Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.

    \-veya -

- Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.

## <a name="use-grammatically-correct-error-messages"></a>Dilbilgisi açısından doğru hata iletilerini kullanma

Açık cümleler yazın ve noktalama işaretlerini sona erdirmeyi içerir. <xref:System.Exception.Message?displayProperty=nameWithType> Özelliğe atanan dizedeki her cümle bir süre içinde sona ermelidir. Örneğin, "Günlük tablosu taşmış." uygun bir ileti dizesi olacaktır.

## <a name="include-a-localized-string-message-in-every-exception"></a>Her özel durum için yerelleştirilmiş bir dize iletisi ekleme

Kullanıcının gördüğü hata iletisi, <xref:System.Exception.Message?displayProperty=nameWithType> özel durum sınıfının adından değil, atılan özel durum özelliğinden türetilmiştir. Genellikle, ileti dizesini bir <xref:System.Exception.Message?displayProperty=nameWithType> [Özel Durum oluşturucunun](xref:System.Exception.%23ctor%2A) `message` bağımsız değişkenine geçirerek özelliğe bir değer atarsınız.

Yerelleştirilmiş uygulamalar için, uygulamanızın atabileceği her özel durum için yerelleştirilmiş bir ileti dizesi sağlamanız gerekir. Yerelleştirilmiş hata iletileri sağlamak için kaynak dosyalarını kullanırsınız. Uygulamaları yerelleştirme ve yerelleştirilmiş dizeleri alma hakkında bilgi için aşağıdaki makalelere bakın:

- [Nasıl yapılır: yerelleştirilmiş özel durum iletileriyle kullanıcı tanımlı özel durumlar oluşturma](how-to-create-localized-exception-messages.md)
- [Masaüstü Uygulamalarında Kaynaklar](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Özel özel durumlarda, gerektiğinde ek özellikler sağlayın

Yalnızca ek bilgilerin yararlı olduğu programlı bir senaryo olduğunda bir özel durum için ek özellikler sağlayın (özel ileti dizesine ek olarak). Örneğin, <xref:System.IO.FileNotFoundException.FileName> özellik <xref:System.IO.FileNotFoundException> sağlar.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Yığın izlemenin yararlı olması için atma deyimleri yerleştirin

Yığın izleme, özel durum atıldığı ifadeden başlar `catch` ve özel durumu yakalayan deyimle sona erer.

## <a name="use-exception-builder-methods"></a>Özel durum oluşturucu yöntemlerini kullanma

Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır. Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın. Örnek:

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

Bazı durumlarda, özel durum oluşturmak için özel durum oluşturucusu kullanmak daha uygundur. Örnek olarak <xref:System.ArgumentException>genel bir özel durum sınıfı.

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a>Özel durumlar nedeniyle yöntemler tamamlanmadığında durumu geri yükleme

Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir. Örneğin, bir hesaptan çekilip başka bir hesaba para yatırarak para aktaran kodunuz varsa ve depozitoyu yürütürlerken bir özel durum atılırsa, para çekme işleminin geçerli kalmasını istemezsinüz.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

Yukarıdaki yöntem doğrudan herhangi bir istisna atmaz, ancak para yatırma işlemi başarısız olursa, para çekme ters böylece savunma yazılmalıdır.

Bu durumu ele almak için bir yolu para yatırma işlemi tarafından atılan herhangi bir istisna yakalamak ve para çekme geri almaktır.

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

Bu örnek, arayanların `throw` <xref:System.Exception.InnerException> özelliği incelemek zorunda kalmadan sorunun gerçek nedenini görmesini kolaylaştıran özgün özel durumu yeniden atma nın kullanımını göstermektedir. Alternatif, yeni bir özel durum atmak ve iç özel durum olarak özgün özel durum eklemektir:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
