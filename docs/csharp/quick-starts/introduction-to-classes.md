---
title: "Sınıfları Öğreticisi - C# yerel quickstarts giriş"
description: "İlk C# programınızı oluşturma ve nesne yönelimli kavramlarını inceleyin"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 97c1de562c86ea04153ec09bb0e813565523a3ba
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="introduction-to-classes"></a>Giriş sınıfları

Bu Hızlı Başlangıç, geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir. Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.

## <a name="create-your-application"></a>Uygulamanızı oluşturun

Bir terminal penceresi kullanarak adlı bir dizin oluşturun **sınıfları**. Uygulamanızı var. oluşturmanız. Bu dizin ve türünü değiştirme `dotnet new console` konsol penceresinde. Bu komut, uygulamanızın oluşturur. Açık **Program.cs**. Aşağıdaki gibi görünmelidir:

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

Bu hızlı başlangıç banka hesabı temsil eden yeni türlerin oluşturacağız. Genellikle geliştiriciler, farklı bir metin dosyasında her sınıfını tanımlar. Bu, bir program boyutu büyüdükçe yönetmenizi kolaylaştırır.  Adlı yeni bir dosya oluşturun **BankAccount.cs** içinde **sınıfları** dizin. 

Bu dosya tanımını içerecek bir ***banka hesabı***. Oriented programlama kodu biçiminde türleri oluşturarak düzenler nesne ***sınıfları***. Bu sınıfları, belirli bir varlık gösteren kodu içerir. `BankAccount` Sınıfı, bir banka hesabı temsil eder. Kod yöntemleri ve özellikleri aracılığıyla belirli işlemlerini uygular. Bu hızlı başlangıç banka hesabı bu davranış destekler:

1. Banka hesabı benzersiz olarak tanıtan 10 basamaklı bir sayı sahiptir.
1. Ad veya adlar sahiplerinin depolayan bir dize içeriyor.
1. Bakiye alınabilir.
1. Bu, mevduatları kabul eder.
1. Bu, çekilen paralar kabul eder.
1. İlk Bakiye pozitif olmalıdır.
1. Çekilen paralar bakiyesi negatif olamaz.

## <a name="define-the-bank-account-type"></a>Banka hesabı türünü tanımlayın

Bu davranışı tanımlayan bir sınıf temelleri oluşturarak başlatabilirsiniz. Şöyle görünür:

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

Geçmeden önce temel aldık bir bakalım.  `namespace` Bildirimi kodunuzu mantıksal olarak düzenlemek için bir yol sağlar. Bir ad alanındaki tüm kod gireceğiniz şekilde bu hızlı başlangıç göreceli olarak azdır. 

`public class BankAccount`sınıf veya türünü tanımlar oluşturmakta olduğunuz. İçindeki tüm öğeler `{` ve `}` sınıfı izleyen bildirimi sınıfı davranışını tanımlar. Beş vardır ***üyeleri*** , `BankAccount` sınıfı. İlk üç olan ***özellikleri***. Özellikler veri öğeleri ve doğrulama veya diğer kurallar zorlar kodu olabilir. Son iki olan ***yöntemleri***. Yöntemleri bu SPN'i tek bir işlev kodu taşlarıdır. Her bir üyesinden adlarını okuma yeterli bilgi veya sınıfı ne yapacağını anlamak için başka bir geliştirici sağlamalıdır.

## <a name="open-a-new-account"></a>Yeni bir hesap açın

Uygulanacak ilk banka hesabı açmak için özelliğidir. Bir müşteri bir hesap oturum açtığında, bir Başlangıç bakiyesi ve sahibi ya da bu hesabı sahipleri hakkında bilgi sağlamanız gerekir. 

Yeni bir nesne oluşturma `BankAccount` türü anlamına gelir tanımlayan bir ***Oluşturucusu*** bu değerleri atar. A ***Oluşturucusu*** sınıf ile aynı ada sahip bir üyesidir. Bu sınıf türü nesnelerin başlatmak için kullanılır. Aşağıdaki oluşturucuyu ekleyin `BankAccount` türü:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Kullanarak bir nesne oluşturduğunuz zaman oluşturucular çağrılır [ `new` ](../language-reference/keywords/new.md). Satır Değiştir `Console.WriteLine("Hello World!");` içinde ***program.cs*** aşağıdaki satırı ile (Değiştir `<name>` adıyla):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Tür `dotnet run` ne olacağını görmek için.  

Hesap numarası boş olduğunu fark ettiniz mi? Bu düzeltme için zaman yapılır. Nesne oluşturulduğunda hesap numarası atanmalıdır. Ancak oluşturmak için arayan sorumluluğunda olmamalıdır. `BankAccount` Sınıf kodu yeni hesap numaraları atama hakkında bilmeniz.  Bunu yapmak için basit bir yol ile 10 basamaklı bir sayı başlatmaktır. Her yeni hesap oluşturulduğunda artırın. Son olarak, bir nesne oluşturulduğunda geçerli hesap numarası depolar.

Aşağıdaki üye bildirimi ekleyin `BankAccount` sınıfı:

```csharp
private static int accountNumberSeed = 1234567890;
```

Bir veri üyesi budur. Bunun `private`, yani yalnızca içinde kod tarafından erişilebilmesini `BankAccount` sınıfı. Bu (hesap numarası sahip gibi) genel Sorumluluklar (hesap numaralarının nasıl oluşturulduğunu.) özel uygulamasından ayırma bir yoludur Oluşturucuya hesap numarası atamak için aşağıdaki iki satırı ekleyin:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Tür `dotnet run` sonuçları görüntüleyin.

## <a name="create-deposits-and-withdrawals"></a>Mevduatlarını ve çekilen paralar oluşturma

Banka hesabı sınıfınız mevduatlarını ve düzgün çalışması için çekilen paralar kabul etmesi gerekir. Şimdi mevduatlarını ve çekilen paralar her işlem hesabı için bir günlük oluşturarak uygular. Bu yalnızca her bir işlem bakiyesi güncelleştirilmesi birkaç avantajı vardır. Geçmiş, tüm işlemler denetim ve günlük bakiyelerini yönetmek için kullanılabilir. Gerektiğinde tüm işlemleri geçmişi Bakiye bilgi işlem tarafından düzeltilen hataları tek bir işlemde doğru bakiyeye üzerinde sonraki hesaplama yansıtılır.

Bir işlem temsil etmek için yeni bir tür oluşturarak başlayalım. Bu herhangi sorumlulukları sahip olmayan basit bir türüdür. Birkaç özelliği gerekir. Adlı yeni bir dosya oluşturun ***Transaction.cs***. Aşağıdaki kodu ekleyin:

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Şimdi, ekleyelim bir <xref:System.Collections.Generic.List%601> , `Transaction` nesneleri `BankAccount` sınıfı. Aşağıdaki bildirimi ekleyin:

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> Sınıfı farklı bir ad alanı almanızı gerektirir. Aşağıdaki başında ekleyin **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Şimdi, değiştirelim nasıl `Balance` bildirilir.  Tüm işlemleri değerlerini toplayarak bulunabilir. Bildirimi değiştirme `Balance` içinde `BankAccount` şu sınıfı:

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Bu örnek, önemli bir yönü gösterir ***özellikleri***. Başka bir programcı değeri sorduğunda Bakiye şimdi bilgi işlem. Hesaplama tüm işlemleri numaralandırır ve toplam olarak geçerli bakiye sağlar.

Ardından, uygulama `MakeDeposit` ve `MakeWithdrawal` yöntemleri. Bu yöntemler son iki kural zorunlu kılacak: ilk Bakiye pozitif olmalıdır ve tüm mevzuatı bakiyesi negatif oluşturmamalıdır. 

Bu kavramı tanıtır ***özel durumları***. Bir yöntem çalışmasını başarıyla tamamlanamıyor belirten standart bir özel durum için yoludur. Özel durum ve onunla ilişkili ileti türünü hata açıklanmaktadır. Burada, `MakeDeposit` yöntemi, banka miktarını negatifse bir özel durum oluşturur. `MakeWithdrawal` Yöntemi mevzuatı tutar negatifse veya mevzuatı uygulama bakiyesi negatif sonuçlanırsa bir özel durum oluşturur:

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[ `throw` ](../language-reference/keywords/throw.md) Deyimi **oluşturur** bir özel durum. Geçerli yönteminin yürütülmesi sona erer ve eşleşen devam edecek `catch` blok bulundu. Ekleyeceksiniz bir `catch` bu kodu biraz daha sonra test etmek için blok.

Böylece Bakiye doğrudan güncelleştirme yerine ilk işlem ekler Oluşturucusu bir değişiklik almanız gerekir. Zaten yazdığınız beri `MakeDeposit` yöntemi, oluşturucudan çağırın. Tamamlanmış oluşturucusu aşağıdaki gibi görünmelidir:

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType>Geçerli tarih ve saati döndürür bir özelliktir. Birkaç mevduatlarını ve içinde çekilen paralar ekleyerek bu test, `Main` yöntemi:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Ardından, bakiyesi negatif olan bir hesap oluşturulmaya çalışılırken tarafından hata koşulları yakalama test edin:

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

Kullandığınız [ `try` ve `catch` deyimleri](../language-reference/keywords/try-catch.md) özel durumlar atabilir kod bloğunu işaretlemek için ve beklediğiniz bu hataları yakalamak için. İçin negatif bir denge oluşturur kodu test etmek için aynı yöntemi kullanabilirsiniz:

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

Dosyayı kaydedip türü `dotnet run` denemek üzere.

## <a name="challenge---log-all-transactions"></a>Sınama - tüm işlemleri günlüğe

Bu hızlı başlangıç tamamlamak için yazabilirsiniz `GetAccountHistory` oluşturan yöntemi bir `string` işlem geçmişi için. Bu yönteme eklemek `BankAccount` türü:

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Bu kullanır <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dize biçimlendirmek için sınıf. Bu hızlı başlangıç ipuçları önceki kodda biçimlendirme dizesi gördünüz. Yeni bir karakter `\t`. Bu çıktı biçimlendirmek için bir sekmesi ekler.

Bunu test etmek için bu satırı ekleyin **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Tür `dotnet run` sonuçları görüntüleyin.

## <a name="next-steps"></a>Sonraki Adımlar

Takılmış, bu hızlı başlangıç kaynağı görebilirsiniz [bizim GitHub depodaki](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)

Tebrikler, bizim Quickstarts tamamladınız. Daha fazla bilgi gezinebileceğinizi, deneyin bizim [öğreticileri](../tutorials/index.md)
