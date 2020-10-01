---
title: Sınıflar ve nesneler-C# öğreticisine giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları keşfedebilirsiniz
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 57394ecb02745d69e22f4d9f1dbd4213f290cd5a
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609056"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="create-your-application"></a>Uygulamanızı oluşturma

Bir Terminal penceresi kullanarak, *sınıflar*adlı bir dizin oluşturun. Uygulamanızı burada oluşturacaksınız. Bu dizine geçin ve `dotnet new console` konsol penceresinde yazın. Bu komut uygulamanızı oluşturur. *Program.cs*'i açın. Şu şekilde görünmelidir:

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

Bu dosya, bir ***Banka hesabının***tanımını içerir. Nesne odaklı programlama, ***sınıf***biçiminde türler oluşturarak kodu düzenler. Bu sınıflar, belirli bir varlığı temsil eden kodu içerir. `BankAccount`Sınıfı bir banka hesabını temsil eder. Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular. Bu öğreticide, banka hesabı bu davranışı destekler:

1. Bu, banka hesabını benzersiz bir şekilde tanımlayan 10 basamaklı bir sayı içerir.
1. Sahiplerinin adını veya adlarını depolayan bir dizesi vardır.
1. Bakiye alınabilir.
1. Mevduat kabul eder.
1. Çekme kabul eder.
1. İlk bakiye pozitif olmalıdır.
1. Çekme işlemleri negatif bir bakiyeye neden olamaz.

## <a name="define-the-bank-account-type"></a>Banka hesap türünü tanımlayın

Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz. **Dosya: New** komutunu kullanarak yeni bir dosya oluşturun. *BankAccount.cs*olarak adlandırın. Aşağıdaki kodu *BankAccount.cs* dosyanıza ekleyin:

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

Başlamadan önce, derleydiklerinize göz atalım.  `namespace`Bildirimi, kodunuzu mantıksal olarak düzenlemek için bir yol sağlar. Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz.

`public class BankAccount` oluşturmakta olduğunuz sınıfı veya türü tanımlar. `{`Sınıf bildirimini izleyen ve içindeki her şey, `}` sınıfının durumunu ve davranışını tanımlar. Sınıfının beş ***üyesi*** vardır `BankAccount` . İlk üçü ***özelliklerdir***. Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir. Son ikisi ***metodlardır***. Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır. Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.

## <a name="open-a-new-account"></a>Yeni bir hesap açın

Uygulanacak ilk özellik bir banka hesabı açmak. Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır.

Türünde yeni bir nesne oluşturmak, `BankAccount` Bu değerleri atayan bir ***Oluşturucu*** tanımlamayı gösterir. ***Oluşturucu*** , sınıfıyla aynı ada sahip olan bir üyedir. Bu sınıf türündeki nesneleri başlatmak için kullanılır. Türe aşağıdaki oluşturucuyu ekleyin `BankAccount` . Aşağıdaki kodu bildiriminin üzerine yerleştirin `MakeDeposit` :

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Oluşturucular, kullanarak bir nesne oluşturduğunuzda çağrılır [`new`](../../language-reference/operators/new-operator.md) . `Console.WriteLine("Hello World!");` *Program.cs* içindeki satırı aşağıdaki kodla değiştirin ( `<name>` adınızla değiştirin):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Şimdiye kadar derlediğiniz şeyi çalıştıralım. Visual Studio kullanıyorsanız, **Çalıştır** menüsünden **hata ayıklama olmadan Başlat** ' ı seçin. Bir komut satırı kullanıyorsanız, `dotnet run` projenizi oluşturduğunuz dizini yazın.

Hesap numarasının boş olduğunu fark muydunuz? Bunun düzeltilmesi zaman alabilir. Nesne oluşturulduğunda hesap numarası atanmalıdır. Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir. `BankAccount`Sınıf kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.  Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır. Her yeni hesap oluşturulduğunda bunu artırın. Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.

Sınıfına bir üye bildirimi ekleyin `BankAccount` . Sınıfın başındaki açılış ayracından sonra aşağıdaki kod satırını yerleştirin `{` `BankAccount` :

```csharp
private static int accountNumberSeed = 1234567890;
```

Bu bir veri üyesidir. Bu `private` , yalnızca sınıfın içindeki kodla erişilebilen anlamına gelir `BankAccount` . Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur. Ayrıca `static` , tüm nesneler tarafından paylaşıldıkları anlamına gelir `BankAccount` . Statik olmayan bir değişkenin değeri, nesnenin her bir örneği için benzersizdir `BankAccount` . Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin. Bu satırları şöyle yerleştir `this.Balance = initialBalance` :

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

`dotnet run`Sonuçları görmek için yazın.

## <a name="create-deposits-and-withdrawals"></a>Mevdular ve çekme işlemleri oluşturma

Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir. Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim. Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar. Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir. Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.

Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım. Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür. Birkaç özelliğe ihtiyaç duyuyor. *Transaction.cs*adlı yeni bir dosya oluşturun. Buna aşağıdaki kodu ekleyin:

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

Şimdi sınıfa bir nesne ekleyelim <xref:System.Collections.Generic.List%601> `Transaction` `BankAccount` . *BankAccount.cs* dosyanızdaki oluşturucudan sonra aşağıdaki bildirimi ekleyin:

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<xref:System.Collections.Generic.List%601>Sınıfı, farklı bir ad alanını içeri aktarmanızı gerektirir. *BankAccount.cs*'nin başlangıcına şunu ekleyin:

```csharp
using System.Collections.Generic;
```

Şimdi, raporun nasıl bildirileceğini değiştirelim `Balance` .  Bu, tüm işlemlerin değerlerini toplayarak bulunabilir. `Balance` `BankAccount` Sınıfında bildirimini aşağıdaki şekilde değiştirin:

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

Bu örnekte, ***özelliklerin***önemli bir yönü gösterilmektedir. Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor. Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.

Sonra, `MakeDeposit` ve yöntemlerini uygulayın `MakeWithdrawal` . Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır.

Bu, ***özel durum***kavramını tanıtır. Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir. Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır. Burada, `MakeDeposit` depozito miktarı negatifse Yöntem bir özel durum oluşturur. `MakeWithdrawal`Çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa Yöntem bir özel durum oluşturur. Listenin bildiriminden sonra aşağıdaki kodu ekleyin `allTransactions` :

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

[`throw`](../../language-reference/keywords/throw.md)İfade bir özel durum **oluşturur** . Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen bloğa yapılan aktarımları denetler `catch` . `catch`Daha sonra bu kodu test etmek için bir blok ekleyeceksiniz.

Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir. Yöntemi zaten yazmış olduğundan `MakeDeposit` , bunu oluşturucudan çağırın. Tamamlanmış Oluşturucu şöyle görünmelidir:

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli tarih ve saati döndüren bir özelliktir. Bu `Main` , yeni bir oluşturan kodun ardından, yönteyinizdeki birkaç mevdug ve çekme bilgilerini ekleyerek test edin `BankAccount` :

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Daha sonra, negatif bakiyeyle bir hesap oluşturmayı deneyerek hata koşullarını yakalamak için test edin. Yeni eklediğiniz kodun ardından aşağıdaki kodu ekleyin:

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

[ `try` Ve `catch` deyimlerini](../../language-reference/keywords/try-catch.md) , özel durum oluşturabilecek bir kod bloğunu işaretlemek ve beklediğinizi bu hataları yakalamak için kullanırsınız. Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz. Yönteminizin sonuna aşağıdaki kodu ekleyin `Main` :

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

Dosyayı kaydedin ve `dotnet run` denemek için yazın.

## <a name="challenge---log-all-transactions"></a>Sınama-tüm işlemleri günlüğe kaydet

Bu öğreticiyi bitirebilmeniz için, `GetAccountHistory` işlem geçmişi için oluşturan yöntemini yazabilirsiniz `string` . Bu yöntemi `BankAccount` türe ekleyin:

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıfını kullanır. Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz. Yeni bir karakter `\t` . Bu, çıktıyı biçimlendirmek için bir sekme ekler.

*Program.cs*içinde test etmek için bu satırı ekleyin:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Sonuçları görmek için programınızı çalıştırın.

## <a name="next-steps"></a>Sonraki adımlar

Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/)deponuzda görebilirsiniz.

[Nesne yönelimli programlama](object-oriented-programming.md) öğreticisiyle devam edebilirsiniz.

Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:

- [If ve else deyimi](../../language-reference/keywords/if-else.md)
- [While ekstresi](../../language-reference/keywords/while.md)
- [Do deyimi](../../language-reference/keywords/do.md)
- [For deyimleri](../../language-reference/keywords/for.md)
