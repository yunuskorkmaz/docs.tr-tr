---
title: Sınıflar ve nesneler- C# öğreticiye giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları gezin
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 092639e86b3e8e683a7d5f6ecf5b732991581b71
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850728"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, yerel geliştirme ortamınızı Mac, PC veya Linux üzerinde ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="create-your-application"></a>Uygulamanızı oluşturma

Bir Terminal penceresi kullanarak, **sınıflar**adlı bir dizin oluşturun. Uygulamanızı burada oluşturacaksınız. Bu dizine geçin ve konsol penceresinde `dotnet new console` yazın. Bu komut uygulamanızı oluşturur. **Program.cs**'i açın. Şu şekilde görünmelidir:

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız. Genellikle geliştiriciler her bir sınıfı farklı bir metin dosyasında tanımlar. Bu, bir program boyutunun büyüdükçe daha kolay yönetilmesini sağlar.  **Classes** dizininde **BankAccount.cs** adlı yeni bir dosya oluşturun. 

Bu dosya, bir ***Banka hesabının***tanımını içerir. Nesne odaklı programlama, ***sınıf***biçiminde türler oluşturarak kodu düzenler. Bu sınıflar, belirli bir varlığı temsil eden kodu içerir. `BankAccount` Sınıfı bir banka hesabını temsil eder. Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular. Bu öğreticide, banka hesabı bu davranışı destekler:

1. Bu, banka hesabını benzersiz bir şekilde tanımlayan 10 basamaklı bir sayı içerir.
1. Sahiplerinin adını veya adlarını depolayan bir dizesi vardır.
1. Bakiye alınabilir.
1. Mevduat kabul eder.
1. Çekme kabul eder.
1. İlk bakiye pozitif olmalıdır.
1. Çekme işlemleri negatif bir bakiyeye neden olamaz.

## <a name="define-the-bank-account-type"></a>Banka hesap türünü tanımlayın

Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz. Şöyle görünür:

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

Başlamadan önce, derleydiklerinize göz atalım.  Bildirimi `namespace` , kodunuzu mantıksal olarak düzenlemek için bir yol sağlar. Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz. 

`public class BankAccount`oluşturmakta olduğunuz sınıfı veya türü tanımlar. Sınıf bildirimini izleyen `{` ve `}` içindeki her şey, sınıfının davranışını tanımlar. `BankAccount` Sınıfının beş ***üyesi*** vardır. İlk üçü ***özelliklerdir***. Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir. Son ikisi ***metodlardır***. Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır. Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.

## <a name="open-a-new-account"></a>Yeni bir hesap açın

Uygulanacak ilk özellik bir banka hesabı açmak. Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır. 

Türünde yeni bir nesne oluşturmak, `BankAccount` bu değerleri atayan bir ***Oluşturucu*** tanımlamayı gösterir. ***Oluşturucu*** , sınıfıyla aynı ada sahip olan bir üyedir. Bu sınıf türündeki nesneleri başlatmak için kullanılır. Aşağıdaki oluşturucuyu `BankAccount` türüne ekleyin:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Oluşturucular, kullanarak [`new`](../../language-reference/operators/new-operator.md)bir nesne oluşturduğunuzda çağrılır. Program.cs içindeki satırı `Console.WriteLine("Hello World!");` aşağıdaki satırla değiştirin (adınızla değiştirin `<name>` ):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Ne `dotnet run` olacağını görmek için yazın.  

Hesap numarasının boş olduğunu fark muydunuz? Bunun düzeltilmesi zaman alabilir. Nesne oluşturulduğunda hesap numarası atanmalıdır. Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir. Sınıf `BankAccount` kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.  Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır. Her yeni hesap oluşturulduğunda bunu artırın. Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.

`BankAccount` Sınıfına aşağıdaki üye bildirimini ekleyin:

```csharp
private static int accountNumberSeed = 1234567890;
```

Bu bir veri üyesidir. Bu, yalnızca `BankAccount` sınıfın içindeki kodla erişilebilen anlamına gelir. `private` Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur. Ayrıca `static`, tüm `BankAccount` nesneler tarafından paylaşıldıkları anlamına gelir. Statik olmayan bir değişkenin değeri, `BankAccount` nesnenin her bir örneği için benzersizdir. Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Sonuçları `dotnet run` görmek için yazın.

## <a name="create-deposits-and-withdrawals"></a>Mevdular ve çekme işlemleri oluşturma

Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir. Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim. Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar. Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir. Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.

Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım. Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür. Birkaç özelliğe ihtiyaç duyuyor. ***Transaction.cs***adlı yeni bir dosya oluşturun. Aşağıdaki kodu buna ekleyin:

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Şimdi <xref:System.Collections.Generic.List%601> sınıfa`BankAccount` bir `Transaction` nesne ekleyelim. Aşağıdaki bildirimi ekleyin:

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

Sınıfı <xref:System.Collections.Generic.List%601> , farklı bir ad alanını içeri aktarmanızı gerektirir. **BankAccount.cs**'nin başlangıcına şunu ekleyin:

```csharp
using System.Collections.Generic;
```

Şimdi, raporun nasıl `Balance` bildirileceğini değiştirelim.  Bu, tüm işlemlerin değerlerini toplayarak bulunabilir. Sınıfında`BankAccount` bildirimini `Balance` aşağıdaki şekilde değiştirin:

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Bu örnekte, ***özelliklerin***önemli bir yönü gösterilmektedir. Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor. Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.

Sonra, `MakeDeposit` ve `MakeWithdrawal` yöntemlerini uygulayın. Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır. 

Bu, ***özel durum***kavramını tanıtır. Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir. Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır. Burada, `MakeDeposit` depozito miktarı negatifse Yöntem bir özel durum oluşturur. Çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa Yöntembirözeldurumoluşturur:`MakeWithdrawal`

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

İfade bir özel durum **oluşturur.** [`throw`](../../language-reference/keywords/throw.md) Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen `catch` bloğa yapılan aktarımları denetler. Daha sonra bu kodu `catch` test etmek için bir blok ekleyeceksiniz.

Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir. `MakeDeposit` Yöntemi zaten yazmış olduğundan, bunu oluşturucudan çağırın. Tamamlanmış Oluşturucu şöyle görünmelidir:

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType>, geçerli tarih ve saati döndüren bir özelliktir. Yönteminizin birkaç mevduyı ve çekme bilgilerini ekleyerek bunu test edin `Main` :

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Daha sonra, negatif bakiyeyle bir hesap oluşturmayı deneyerek hata koşullarını yakalama konusunda test edin:

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

[ `try` Ve deyimlerini,özeldurumoluşturabilecekbirkodbloğunuişaretlemekvebeklediğinizibuhatalarıyakalamakiçinkullanırsınız.`catch` ](../../language-reference/keywords/try-catch.md) Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz:

```csharp
// Test for a negative balance:
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Dosyayı kaydedin ve denemek için `dotnet run` yazın.

## <a name="challenge---log-all-transactions"></a>Sınama-tüm işlemleri günlüğe kaydet

Bu öğreticiyi bitirebilmeniz için, işlem geçmişi `GetAccountHistory` `string` için oluşturan yöntemini yazabilirsiniz. Bu yöntemi `BankAccount` türe ekleyin:

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıfını kullanır. Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz. Yeni bir karakter `\t`. Bu, çıktıyı biçimlendirmek için bir sekme ekler.

**Program.cs**içinde test etmek için bu satırı ekleyin:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Sonuçları `dotnet run` görmek için yazın.

## <a name="next-steps"></a>Sonraki Adımlar

Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/) deponuzda görebilirsiniz

Tebrikler, C# öğreticilere giriş yaptığımızı tamamladınız. Daha fazla bilgi edinmek istiyorsanız [öğreticilerimizi](../index.md) deneyin
