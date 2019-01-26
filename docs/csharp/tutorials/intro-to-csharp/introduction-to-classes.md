---
title: Sınıflar ve nesneler - giriş C# Öğreticisi
description: İlk C# programınızı oluşturma ve nesne yönelimli kavramları keşfedin
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 6ce0c86a4b746b8ea2db82899a82734a68e46957
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066079"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Nesne yönelimli programlama ile ilgili sınıfları ve nesneleri keşfedin

Bu öğreticide, geliştirme için kullanabileceğiniz bir makine olmasını bekliyor. .NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte.

## <a name="create-your-application"></a>Uygulamanızı oluşturma

Bir terminal penceresinde kullanarak adlı bir dizin oluşturma **sınıfları**. Uygulamanız var. oluşturacaksınız. Bu dizin ve türü değiştirme `dotnet new console` konsol penceresinde. Bu komut, uygulamanızı oluşturur. Açık **Program.cs**. Şu şekilde görünmelidir:

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

Bu öğreticide, bir banka hesabı temsil eden yeni türler oluşturacağız. Genellikle geliştiriciler, farklı metin dosyasında her sınıfı tanımlayın. Bu, bir program boyutu büyüdükçe yönetmenizi kolaylaştırır.  Adlı yeni bir dosya oluşturun **BankAccount.cs** içinde **sınıfları** dizin. 

Bu dosya tanımını içerecek bir ***banka hesabı***. Oriented programlama biçiminde türleri oluşturarak kodu düzenler nesne ***sınıfları***. Bu sınıflar, belirli bir varlığı temsil eden kodu bulunur. `BankAccount` Sınıfı, bir banka hesabı temsil eder. Kod, yöntemleri ve özellikleri aracılığıyla belirli işlemler uygular. Bu öğreticide, bu davranışı banka hesabı destekler:

1. Banka hesabı benzersiz olarak tanımlayan 10 basamaklı bir sayı var.
1. Adı veya adları sahiplerinin depolayan bir dize var.
1. Bakiye alınabilir.
1. Bu, mevduatları kabul eder.
1. Bunun çekilen paralar kabul eder.
1. Başlangıç bakiyesi pozitif olmalıdır.
1. Çekilen paralar negatif bakiyeye sonuçlanmaz.

## <a name="define-the-bank-account-type"></a>Banka hesabı türünü tanımlayın

Bu davranışı tanımlayan bir sınıf temelleri oluşturarak başlayabilirsiniz. Şöyle görünebilir:

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

Geçmeden önce şimdi ne derlediğiniz bir göz atalım.  `namespace` Bildirimi kodunuzu mantıksal olarak düzenlemek için bir yol sağlar. Bu öğreticide görece küçük olduğundan bir ad alanındaki tüm kod giriyorum. 

`public class BankAccount` sınıf veya tür, tanımlar oluşturuyorsunuz. İçindeki her şey `{` ve `}` , sınıf aşağıdaki bildirimi, sınıf davranışını tanımlar. Beş vardır ***üyeleri*** , `BankAccount` sınıfı. İlk üç olan ***özellikleri***. Özellikler veri öğelerini ve doğrulama veya diğer kuralları zorlar kodu oluşturmasını sağlayabilirsiniz. Son iki olan ***yöntemleri***. Tek bir işlevi gerçekleştiren kod blokları yöntemlerdir. Her üye adlarını okuma yeterli bilgi veya sınıf ne yaptığını anlamak için başka bir geliştirici sağlamanız gerekir.

## <a name="open-a-new-account"></a>Yeni hesabı açın

İlk özellik uygulamak için bir banka hesabı açmaktır. Bir müşteri bir hesap oturum açtığında, bir Başlangıç bakiyesi ve sahip veya bu hesap sahipleri hakkında bilgi sağlamanız gerekir. 

Yeni bir nesne oluşturma `BankAccount` türü anlamına gelir tanımlayan bir ***Oluşturucusu*** bu değerleri atar. A ***Oluşturucusu*** sınıfı aynı ada sahip bir üyesidir. Bu sınıf türü nesnelerini başlatmak için kullanılır. Aşağıdaki oluşturucuyu ekleyin `BankAccount` türü:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Oluşturucuları kullanarak bir nesne oluşturduğunuzda çağrılır [ `new` ](../../language-reference/keywords/new.md). Satırı değiştirin `Console.WriteLine("Hello World!");` içinde ***program.cs*** aşağıdaki satırı ile (Değiştir `<name>` adınızla):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Tür `dotnet run` ne olacağını görmek için.  

Hesap numarası boş olduğunu fark ettiniz mi? Buna, süreyi var. Nesne oluşturulduğunda, hesap numarası atanmalıdır. Ancak, arayanın oluşturmak için sorumluluk olmamalıdır. `BankAccount` Sınıf kodunu, yeni hesap numaraları atama bilmelidir.  Bunu yapmak için basit bir yol ile 10 basamaklı bir sayı başlatmaktır. Her yeni bir hesap oluşturulduğunda, artırın. Son olarak, bir nesne oluşturulduğunda geçerli hesap numarası depolayın.

Aşağıdaki üye bildirimi için ekleme `BankAccount` sınıfı:

```csharp
private static int accountNumberSeed = 1234567890;
```

Bir veri üyesi budur. Sahip `private`, yani yalnızca içinde kod tarafından erişilebilir `BankAccount` sınıfı. (Bir hesap numarası sahip gibi) genel Sorumluluklar (nasıl hesap numaraları oluşturulur.) özel uygulamadan ayırma bir yoludur Ayrıca `static`, yani tüm tarafından paylaşılan `BankAccount` nesneleri. Statik olmayan bir değişkenin değerini her örneği için benzersiz olan `BankAccount` nesne. Aşağıdaki iki satırı hesabı atamak için oluşturucuyu ekleyin:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Tür `dotnet run` sonuçları görmek için.

## <a name="create-deposits-and-withdrawals"></a>Mevduatlarını ve çekilen paralar oluşturma

Banka hesabı sınıfınıza mevduatlarını ve düzgün çalışması için çekilen paralar kabul etmeniz gerekir. Şimdi mevduatlarını ve çekilen paralar sefer hesabı için bir günlük oluşturarak uygulayın. Her işlem bakiyeye güncelleştirerek kolayca bazı avantajları vardır. Geçmiş, tüm işlemler denetim ve günlük bakiyeleri yönetmek için kullanılabilir. Gerektiğinde tüm işlemleri geçmişini bakiyeden bilgi işlem tarafından düzeltilen hataları tek bir işlemde doğru dengesi üzerinde sonraki hesaplama yansıtılır.

Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım. Bu tüm Sorumluluklar sahip olmayan basit bir türdür. Bunun birkaç özellik gerekir. Adlı yeni bir dosya oluşturun ***Transaction.cs***. Aşağıdaki kodu ekleyin:

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Şimdi, ekleyelim bir <xref:System.Collections.Generic.List%601> , `Transaction` nesneleri için `BankAccount` sınıfı. Aşağıdaki bildirimi ekleyin:

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Sınıfı farklı bir ad alanı almanızı gerektirir. Başında ekleyin **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Şimdi, değiştirelim nasıl `Balance` bildirilir.  Tüm işlemlerin değerleri toplayarak bulunabilir. Değiştirin `Balance` içinde `BankAccount` aşağıdaki sınıfı:

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Bu örnek, önemli bir yönüdür gösterir ***özellikleri***. Başka bir programcı değeri sorduğunda Bakiye artık bilgi işlem. Kendi hesaplama tüm işlemleri numaralandırır ve toplam tutar kadar sağlar.

Ardından, uygulama `MakeDeposit` ve `MakeWithdrawal` yöntemleri. Son iki kural bu yöntemlerin kullanılmasını zorunlu: Başlangıç bakiyesi pozitif ve negatif bir denge herhangi mevzuatı oluşturmamalıdır. 

Bu kavramı tanıtır ***özel durumları***. Bir yöntem işini başarıyla tamamlanamıyor belirten standart bir özel durum için yoludur. Özel durum ve onunla ilişkili ileti türünü hata açıklanmaktadır. Burada, `MakeDeposit` yöntemi havale miktarını negatif ise bir özel durum oluşturur. `MakeWithdrawal` Mevzuatı tutar negatif ise ya da uygulama mevzuatı negatif bakiyeye sonuçlanırsa yöntemi bir özel durum oluşturur:

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../../language-reference/keywords/throw.md) Deyimi **oluşturur** bir özel durum. Geçerli yürütme engelleme sona erer ve denetim ilk eşleştirme aktarımları `catch` blok çağrı yığınında bulunamadı. Ekleyeceğiniz bir `catch` Bu kod biraz daha sonra test etmek için blok.

Oluşturucu, Bakiye doğrudan güncelleştirmek yerine bir ilk işlem ekler, böylece bir değişiklik almanız gerekir. Zaten yazdığınız beri `MakeDeposit` yöntemi, oluşturucudan çağırın. Tamamlanmış Oluşturucusu gibi görünmelidir:

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> Geçerli tarih ve saati döndürür bir özelliktir. Birkaç mevduatlarını ve de çekilen paralar ekleyerek bu test, `Main` yöntemi:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Ardından, negatif bakiyesi olan bir hesap oluşturulmaya çalışılırken tarafından hata koşulları yakalama test edin:

```csharp
// Test that the initial balances must be positive:
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

Kullandığınız [ `try` ve `catch` deyimleri](../../language-reference/keywords/try-catch.md) bir özel durum oluşturabildiğini varsaymasını kod bloğu işaretlemek için ve beklediğiniz bu hataları yakalamak için. Bir negatif dengelemek için bir özel durum kodu test etmek için aynı tekniği kullanabilirsiniz:

```csharp
// Test for a negative balance
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

Dosya ve tür Kaydet `dotnet run` denemek için.

## <a name="challenge---log-all-transactions"></a>Sınaması - tüm işlemlerini günlüğe kaydet

Bu öğreticiyi tamamlamak için şunu yazabilirsiniz `GetAccountHistory` oluşturan yöntemine bir `string` işlem geçmişi. Bu yönteme ekleme `BankAccount` türü:

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Bu kullanır <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıf. Bu öğreticileri, kod biçimlendirme dizesi gördünüz. Yeni bir karakter `\t`. Çıktıyı biçimlendirmek için bir sekme ekler.

Bunu test etmek için bu satırı ekleyin **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Tür `dotnet run` sonuçları görmek için.

## <a name="next-steps"></a>Sonraki Adımlar

Takılı, Bu öğretici için kaynak görebilirsiniz [GitHub depomuz içinde](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)

Tebrikler, sunduğumuz tüm giriş bitirdikten C# öğreticiler. Daha fazla bilgi edinmek için, daha fazlasını deneyin bizim [öğreticiler](../index.md)
