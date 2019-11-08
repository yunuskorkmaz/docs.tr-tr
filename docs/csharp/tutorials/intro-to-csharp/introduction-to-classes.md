---
title: Sınıflar ve nesneler- C# öğreticiye giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları gezin
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: e4cf7912de69946289c0594944b8ac3a8c252ac2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736834"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="create-your-application"></a>Uygulamanızı oluşturma

Bir Terminal penceresi kullanarak, *sınıflar*adlı bir dizin oluşturun. Uygulamanızı burada oluşturacaksınız. Bu dizine geçin ve konsol penceresinde `dotnet new console` yazın. Bu komut uygulamanızı oluşturur. *Program.cs*'i açın. Şöyle görünmelidir:

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

Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız. Genellikle geliştiriciler her bir sınıfı farklı bir metin dosyasında tanımlar. Bu, bir program boyutunun büyüdükçe daha kolay yönetilmesini sağlar. *Classes* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun. 

Bu dosya, bir ***Banka hesabının***tanımını içerir. Nesne odaklı programlama, ***sınıf***biçiminde türler oluşturarak kodu düzenler. Bu sınıflar, belirli bir varlığı temsil eden kodu içerir. `BankAccount` sınıfı bir banka hesabını temsil eder. Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular. Bu öğreticide, banka hesabı bu davranışı destekler:

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

Başlamadan önce, derleydiklerinize göz atalım.  `namespace` bildirimi, kodunuzu mantıksal olarak düzenlemek için bir yol sağlar. Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz. 

`public class BankAccount` oluşturduğunuz sınıfı veya türü tanımlar. Sınıf bildirimini izleyen `{` ve `}` içindeki her şey, sınıfının davranışını tanımlar. `BankAccount` sınıfının beş ***üyesi*** vardır. İlk üçü ***özelliklerdir***. Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir. Son ikisi ***metodlardır***. Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır. Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.

## <a name="open-a-new-account"></a>Yeni bir hesap açın

Uygulanacak ilk özellik bir banka hesabı açmak. Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır. 

`BankAccount` türünde yeni bir nesne oluşturmak, bu değerleri atayan bir ***oluşturucunun*** tanımlanması anlamına gelir. ***Oluşturucu*** , sınıfıyla aynı ada sahip olan bir üyedir. Bu sınıf türündeki nesneleri başlatmak için kullanılır. `BankAccount` türüne aşağıdaki oluşturucuyu ekleyin:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Oluşturucular, [`new`](../../language-reference/operators/new-operator.md)kullanarak bir nesne oluşturduğunuzda çağrılır. *Program.cs* içindeki satır `Console.WriteLine("Hello World!");` aşağıdaki satırla değiştirin (`<name>` adını adınızla değiştirin):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Ne olacağını görmek için `dotnet run` yazın.  

Hesap numarasının boş olduğunu fark muydunuz? Bunun düzeltilmesi zaman alabilir. Nesne oluşturulduğunda hesap numarası atanmalıdır. Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir. `BankAccount` sınıfı kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.  Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır. Her yeni hesap oluşturulduğunda bunu artırın. Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.

`BankAccount` sınıfına aşağıdaki üye bildirimini ekleyin:

```csharp
private static int accountNumberSeed = 1234567890;
```

Bu bir veri üyesidir. `private`, bu, yalnızca `BankAccount` sınıfının içindeki kodla erişilebileceği anlamına gelir. Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur. Ayrıca `static`, bu, tüm `BankAccount` nesneleri tarafından paylaşıldığını gösterir. Statik olmayan bir değişkenin değeri, `BankAccount` nesnesinin her bir örneği için benzersizdir. Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Sonuçları görmek için `dotnet run` yazın.

## <a name="create-deposits-and-withdrawals"></a>Mevdular ve çekme işlemleri oluşturma

Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir. Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim. Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar. Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir. Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.

Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım. Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür. Birkaç özelliğe ihtiyaç duyuyor. *Transaction.cs*adlı yeni bir dosya oluşturun. Aşağıdaki kodu buna ekleyin:

[!code-csharp[Transaction](~/samples/csharp/classes-quickstart/Transaction.cs)]

Şimdi, `BankAccount` sınıfına `Transaction` nesnelerinin <xref:System.Collections.Generic.List%601> ekleyelim. Aşağıdaki bildirimi ekleyin:

[!code-csharp[TransactionDecl](~/samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<xref:System.Collections.Generic.List%601> sınıfı, farklı bir ad alanını içeri aktarmanızı gerektirir. *BankAccount.cs*'nin başlangıcına şunu ekleyin:

```csharp
using System.Collections.Generic;
```

Şimdi `Balance` raporlanmasını değiştirelim.  Bu, tüm işlemlerin değerlerini toplayarak bulunabilir. `BankAccount` sınıfındaki `Balance` bildirimini aşağıdaki şekilde değiştirin:

[!code-csharp[BalanceComputation](~/samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

Bu örnekte, ***özelliklerin***önemli bir yönü gösterilmektedir. Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor. Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.

Sonra, `MakeDeposit` ve `MakeWithdrawal` yöntemlerini uygulayın. Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır. 

Bu, ***özel durum***kavramını tanıtır. Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir. Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır. Burada, depozito miktarı negatifse `MakeDeposit` yöntemi bir özel durum oluşturur. `MakeWithdrawal` yöntemi, çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa bir özel durum oluşturur:

[!code-csharp[DepositAndWithdrawal](~/samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

[`throw`](../../language-reference/keywords/throw.md) deyimleri bir özel durum **oluşturur** . Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen `catch` bloğuna denetim aktarımları yapılır. Daha sonra bu kodu test etmek için bir `catch` bloğu ekleyeceksiniz.

Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir. `MakeDeposit` yöntemini zaten yazmış olduğunuz için oluşturucudan çağırın. Tamamlanmış Oluşturucu şöyle görünmelidir:

[!code-csharp[Constructor](~/samples/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType>, geçerli tarih ve saati döndüren bir özelliktir. `Main` yönteyinizdeki birkaç mevdua ve çekme bilgilerini ekleyerek bunu test edin:

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

Özel durum oluşturabilecek bir kod bloğunu işaretlemek ve istediğiniz hataları yakalamak için [`try` ve `catch` deyimlerini](../../language-reference/keywords/try-catch.md) kullanın. Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz:

```csharp
// Test for a negative balance.
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

Bu öğreticiyi bitirebilmeniz için, işlem geçmişi için bir `string` oluşturan `GetAccountHistory` yöntemi yazabilirsiniz. Bu yöntemi `BankAccount` türüne ekleyin:

[!code-csharp[History](~/samples/csharp/classes-quickstart/BankAccount.cs#History)]

Bu, her işlem için bir satır içeren bir dizeyi biçimlendirmek için <xref:System.Text.StringBuilder> sınıfını kullanır. Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz. Yeni bir karakter `\t`. Bu, çıktıyı biçimlendirmek için bir sekme ekler.

*Program.cs*içinde test etmek için bu satırı ekleyin:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Sonuçları görmek için `dotnet run` yazın.

## <a name="next-steps"></a>Sonraki adımlar

Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)deponuzda görebilirsiniz.

Tebrikler, C# öğreticilere giriş yaptığımızı tamamladınız. Daha fazla bilgi edinmek istiyorsanız [öğreticilerimizi](../index.md)deneyin.
