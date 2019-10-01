---
title: Özel durumlar için en iyi uygulamalar-.NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 6a165c3e0f41603ef7233669d7148dd44b1d3ce6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696759"
---
# <a name="best-practices-for-exceptions"></a>Özel durumlar için en iyi uygulamalar

İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler. Bu bölümde, özel durumları işlemeye ve oluşturmaya yönelik en iyi uygulamalar açıklanmaktadır.

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a>Hataları veya yayın kaynaklarını kurtarmak için try/catch/finally bloklarını kullanın

Büyük olasılıkla bir özel durum oluşturabilen ***ve*** kodunuzun bu özel durumdan kurtulabildiği kod etrafında `try` @ no__t-1 @ no__t-2 blok kullanın. @No__t-0 blokları ' nda, her zaman en çok türetilen özel durumları en düşük türetilmiş öğesine sıralayın. Tüm özel durumlar <xref:System.Exception> ' dan türetilir. Daha önce türetilmiş özel durumlar, bir temel özel durum sınıfı için catch yan tümcesinin önünde bulunan bir catch yan tümcesi tarafından işlenmez. Kodunuz bir özel durumdan kurtarılamadığında bu özel durumu yakalamayın. Mümkünse, çağrı yığınını daha sonra kurtarmak için yöntemleri etkinleştirin.

@No__t-0 deyimleriyle veya `finally` bloğuyla ayrılan kaynakları temizleyin. Özel durumlar oluştuğunda kaynakları otomatik olarak temizlemek için `using` deyimlerini tercih edin. @No__t-1 ' i uygulamayan kaynakları temizlemek için `finally` blokları kullanın. @No__t-0 yan tümcesindeki kod, özel durumlar oluştuğunda bile neredeyse her zaman yürütülür.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Özel durumlar oluşturmadan ortak koşulları işleme

Meydana gelen ancak özel durum tetikleyebilen koşullar için, özel durumu önlemek için bunları işlemeyi göz önünde bulundurun. Örneğin, zaten kapatılmış olan bir bağlantıyı kapatmaya çalışırsanız, bir @no__t (0) alırsınız. Kapatmayı denemeden önce bağlantı durumunu denetlemek için `if` ifadesini kullanarak bundan kaçınabilirsiniz.

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

Kapatmadan önce bağlantı durumunu denetmezseniz, `InvalidOperationException` özel durumunu yakalayabilirsiniz.

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

Seçme yöntemi, olayın ne sıklıkta gerçekleşmesini beklediğinize bağlıdır.

- Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın. Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.

- Olay düzenli olarak gerçekleşdiğinde ve normal yürütmenin parçası olarak kabul edildiğinde koddaki hata koşullarını denetleyin. Yaygın hata koşullarını denetlediğinizde, özel durumların önüne düşeceğinden daha az kod yürütülür.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Özel durumların önlenebilir olması için sınıfları tasarlayın

Bir sınıf, özel durum tetikleyebilecek bir çağrı yapmaktan kaçınmanızı sağlayan yöntemler veya özellikler sağlayabilir. Örneğin, <xref:System.IO.FileStream> sınıfı, dosyanın sonuna ulaşılıp ulaşılmadığını belirlemenize yardımcı olan yöntemler sağlar. Bunlar, dosyanın sonundan sonra okuduğunuzda oluşturulan özel durumu önlemek için kullanılabilir. Aşağıdaki örnek, bir özel durum tetiklemeden bir dosyanın sonuna nasıl okunacağını gösterir.

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

Özel durumların önlenmesi için başka bir yol da, özel durum oluşturmak yerine son derece yaygın hata durumları için null (veya varsayılan) döndürmaktır. Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir. Bu durumlarda null (veya varsayılan) döndürerek, bir uygulamaya yönelik performans etkisini en aza indirmiş olursunuz.

Değer türleri için `Nullable<T>` ' ı mi yoksa varsayılan olarak, hata göstergesi ise, belirli bir uygulamanız için göz önünde bulundurmanız gereken bir şeydir) kullanın. @No__t-0 ' ı kullanarak `default` `Guid.Empty` yerine `null` olur. @No__t-0 eklemek, bir değer varsa veya olmadığında daha net hale gelir. Diğer zamanlarda `Nullable<T>` eklemek, gerekli olmadığını denetlemek için ek durumlar oluşturabilir ve yalnızca olası hata kaynakları oluşturmak için bu hizmeti sunar. 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Hata kodu döndürmek yerine özel durumlar oluşturun

Özel durumlar, çağrı kodu bir dönüş kodunu denetlemediğinden hataların açıklanmamasının algılanmadığından emin olun.

## <a name="use-the-predefined-net-exception-types"></a>Önceden tanımlanmış .NET özel durum türlerini kullanın

Yalnızca önceden tanımlanmış bir uygulama uygulanmazsa yeni bir özel durum sınıfı tanıtın. Örneğin:

- Bir özellik kümesi veya yöntem çağrısı nesnenin geçerli durumuna uygun değilse, <xref:System.InvalidOperationException> özel durumu oluşturur.

- Geçersiz parametreler geçirilirse <xref:System.ArgumentException> özel durumu veya <xref:System.ArgumentException> ' den türetilen önceden tanımlanmış sınıflardan birini oluşturur.

## <a name="end-exception-class-names-with-the-word-exception"></a>Özel durum sınıfı adlarını @no__t kelimeyle Sonlandır-0

Özel bir özel durum gerekli olduğunda, bunu uygun şekilde adlandırın ve <xref:System.Exception> sınıfından türetirsiniz. Örneğin:

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a>Özel özel durum sınıflarında üç Oluşturucu Ekle

Kendi özel durum sınıflarınızı oluştururken en az üç ortak Oluşturucu kullanın: parametresiz Oluşturucu, bir dize iletisi alan Oluşturucu ve bir dize iletisi ve bir iç özel durum alan Oluşturucu.

- varsayılan değerleri kullanan <xref:System.Exception.%23ctor>.

- <xref:System.Exception.%23ctor%28System.String%29>, bir dize iletisi kabul eder.

- <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, bir dize iletisi ve bir iç özel durum kabul eder.

Bir örnek için bkz. [nasıl yapılır: Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Kod uzaktan yürütüldüğünde özel durum verilerinin kullanılabilir olduğundan emin olun

Kullanıcı tanımlı özel durumlar oluştururken, özel durumlar için meta verilerin uzaktan yürütülen kod için kullanılabilir olduğundan emin olun.

Örneğin, uygulama etki alanlarını destekleyen .NET uygulamalarında, uygulama etki alanları arasında özel durumlar oluşabilir. Uygulama etki alanı A 'nın bir özel durum oluşturan kodu çalıştıran bir uygulama etki alanı oluşturduğunu varsayalım. Uygulama etki alanı A 'nın özel durumu doğru bir şekilde yakalayabilmesi ve işlemesi için, uygulama etki alanı B tarafından oluşturulan özel durumu içeren derlemeyi bulması gerekir. Uygulama etki alanı B, uygulama temeli altındaki bir derlemede bulunan ancak uygulama etki alanı A 'nın uygulama temeli altında olmayan bir özel durum oluşturursa, A uygulama etki alanı özel durumu bulamaz ve ortak dil çalışma zamanı <xref:System.IO.FileNotFoundException> özel durumu oluşturur. Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:

- Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.

    \- veya-

- Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.

## <a name="use-grammatically-correct-error-messages"></a>Dilsiz doğru hata iletilerini kullanma

Temiz cümleler yazın ve son noktalama işaretlerini ekleyin. @No__t-0 özelliğine atanan dizedeki her tümce bir noktayla bitmelidir. Örneğin, "günlük tablosu taşmıştır." uygun bir ileti dizesi olacaktır.

## <a name="include-a-localized-string-message-in-every-exception"></a>Her özel duruma yerelleştirilmiş bir dize iletisi ekleyin

Kullanıcının gördüğü hata iletisi, özel durum sınıfının adından değil, oluşturulan özel durumun <xref:System.Exception.Message?displayProperty=nameWithType> özelliğinden türetilir. Genellikle, ileti dizesini bir [özel durum oluşturucusunun](xref:System.Exception.%23ctor%2A)`message` bağımsız değişkenine geçirerek <xref:System.Exception.Message?displayProperty=nameWithType> özelliğine bir değer atarsınız.

Yerelleştirilmiş uygulamalar için, uygulamanızın oluşturabildiğini her özel durum için yerelleştirilmiş bir ileti dizesi sağlamalısınız. Yerelleştirilmiş hata iletileri sağlamak için kaynak dosyalarını kullanırsınız. Uygulamaları Yerelleştirme ve yerelleştirilmiş dizeleri alma hakkında bilgi için aşağıdaki makalelere bakın:

- [Nasıl yapılır: yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-localized-exception-messages.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../framework/resources/index.md) 
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Özel özel durumlarda, gerektiğinde ek özellikler sağlayın

Özel durum için ek özellikler sağlayın (özel ileti dizesine ek olarak), yalnızca ek bilgilerin yararlı olduğu bir programlama senaryosu varsa. Örneğin, <xref:System.IO.FileNotFoundException> <xref:System.IO.FileNotFoundException.FileName> özelliğini sağlar.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Yığın izlemenin yararlı olacağı şekilde throw deyimlerini yerleştirin

Yığın izlemesi özel durumun oluşturulduğu deyimden başlar ve özel durumu yakalayan `catch` ifadesinde biter.

## <a name="use-exception-builder-methods"></a>Özel durum Oluşturucu yöntemlerini kullanın

Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır. Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın. Örneğin:

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

Bazı durumlarda, özel durumu oluşturmak için özel durumun oluşturucusunu kullanmak daha uygundur. Örnek, <xref:System.ArgumentException> gibi genel bir özel durum sınıfıdır.

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a>Yöntemler özel durumlar nedeniyle tamamlanmadığınızda durumu geri yükle

Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir. Örneğin, bir hesaptan withdrawing ve başka bir hesapta bir özel durum oluşturan bir kod varsa ve depozito yürütülürken bir özel durum oluşturulursa, çekme al 'nın etkin kalmasını istemezsiniz.

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

Yukarıdaki yöntem, doğrudan özel durum oluşturmaz, ancak depozito işlemi başarısız olursa, çekme işleminin ters çevrilmesiyle yeniden savunma yapılmalıdır.

Bu durumu işlemenin bir yolu, depozito işlemi tarafından oluşturulan tüm özel durumları yakalamak ve geri alma işlemini geri almak olur.

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

Bu örnek, özgün özel durumu yeniden oluşturmak için `throw` kullanımını gösterir. Bu, çağıranların, <xref:System.Exception.InnerException> özelliğini incelemek zorunda kalmadan sorunun gerçek nedenini görmesini kolaylaştırır. Diğer bir seçenek de yeni bir özel durum oluşturmak ve asıl özel durumu iç özel durum olarak içerkullanmaktır:

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

- [Özel Durumlar](index.md)
