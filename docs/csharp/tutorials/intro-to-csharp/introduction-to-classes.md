---
title: Sınıflar ve nesneler - C# eğitimine giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları keşfedin
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: b6ad72997647b80b981f1a1871e384791404bdf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156599"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Sınıflar ve nesnelerle nesne yönelimli programlamayı keşfedin

Bu öğretici, geliştirme için kullanabileceğiniz bir makineniz olmasını bekler. .NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir. Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md) dır.

## <a name="create-your-application"></a>Uygulamanızı oluşturun

Terminal pencereyi kullanarak, *sınıflar*adlı bir dizin oluşturun. Başvurunuzu orada oluşturacaksınız. Bu dizini değiştirin `dotnet new console` ve konsol penceresine yazın. Bu komut uygulamanızı oluşturur. Açık *Program.cs*. Şu şekilde görünmelidir:

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

Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız. Genellikle geliştiriciler her sınıfı farklı bir metin dosyasında tanımlar. Bu, bir programın boyutu arttıkça yönetimi kolaylaştırır. *Sınıflar* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun.

Bu dosya bir banka ***hesabının***tanımını içerecektir. Nesne Yönelimli programlama ***sınıflar***şeklinde türleri oluşturarak kodu düzenler. Bu sınıflar belirli bir varlığı temsil eden kodu içerir. Sınıf `BankAccount` bir banka hesabını temsil eder. Kod, yöntemler ve özellikler aracılığıyla belirli işlemleri uygular. Bu öğreticide, banka hesabı bu davranışı destekler:

1. Banka hesabını benzersiz olarak tanımlayan 10 basamaklı bir numarası vardır.
1. Sahiplerinin adlarını veya adlarını depolayan bir dize vardır.
1. Bakiye alınabilir.
1. Depozito kabul ediyor.
1. Para çekmeyi kabul ediyor.
1. İlk denge pozitif olmalıdır.
1. Para çekme işlemi negatif bir denge yle sonuçlanamaz.

## <a name="define-the-bank-account-type"></a>Banka hesap türünü tanımlama

Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz. Bu gibi görünecek:

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

Devam etmeden önce, ne inşa ettiğinize bir göz atalım.  Bildirim, `namespace` kodunuzu mantıksal olarak düzenlemek için bir yol sağlar. Bu öğretici nispeten küçüktür, bu nedenle tüm kodu tek bir ad alanına koyarsınız.

`public class BankAccount`oluşturduğunuz sınıfı veya türü tanımlar. Sınıf `{` bildiriminin `}` içindeki ve izleyen her şey sınıfın durumunu ve davranışını tanımlar. Sınıfın beş üyesi var. ***members*** `BankAccount` İlk üçü ***özellikleridir.*** Özellikler veri öğeleridir ve doğrulama yı veya diğer kuralları zorlayan bir koda sahip olabilir. Son iki ***yöntem***dir. Yöntemler, tek bir işlev icra eden kod bloklarıdır. Üyelerin her birinin adlarını okumak, sınıfın ne yaptığını anlamak için sizin veya başka bir geliştiriciiçin yeterli bilgi sağlamalıdır.

## <a name="open-a-new-account"></a>Yeni bir hesap açma

Uygulanacak ilk özellik bir banka hesabı açmaktır. Bir müşteri bir hesap açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlaması gerekir.

`BankAccount` Türünden yeni bir nesne oluşturmak, bu değerleri atayan bir ***oluşturucu*** tanımlama anlamına gelir. ***Oluşturucu,*** sınıfla aynı ada sahip bir üyedir. Bu sınıf türünesneleri başlatılması için kullanılır. Türüne aşağıdaki oluşturucu `BankAccount` ekleyin:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Bir nesne oluşturduğunuzda yapıcılar [`new`](../../language-reference/operators/new-operator.md)çağrılır. `Console.WriteLine("Hello World!");` satırı *Program.cs* aşağıdaki kodla değiştirin `<name>` (adınız ile değiştirin):

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Ne `dotnet run` olacağını görmek için yazın.  

Hesap numarasının boş olduğunu fark ettin mi? Bunu düzeltmenin zamanı oldu. Nesne oluşturulduğunda hesap numarası atanmalıdır. Ama onu oluşturmak arayan kişinin sorumluluğu nda olmamalıdır. Sınıf `BankAccount` kodu yeni hesap numaraları atamayı bilmelidir.  Bunu yapmanın basit bir yolu 10 basamaklı bir sayı ile başlamaktır. Her yeni hesap oluşturulduğunda artım. Son olarak, bir nesne oluşturulduğunda cari hesap numarasını depolayın.

Sınıfa aşağıdaki üye `BankAccount` bildirimini ekleyin:

```csharp
private static int accountNumberSeed = 1234567890;
```

Bu bir veri üyesi. Yani `private`sadece `BankAccount` sınıf içindeki kodla erişilebiliyor. Bu, genel sorumlulukları (hesap numarasına sahip olmak gibi) özel uygulamadan (hesap numaralarının nasıl oluşturulduğunu) ayırmanın bir yoludur. Aynı zamanda, `static`tüm `BankAccount` nesneler tarafından paylaşılır anlamına gelir. Statik olmayan bir değişkenin değeri `BankAccount` nesnenin her örneğine özgüdür. Hesap numarasını atamak için aşağıdaki iki satırı oluşturucuya ekleyin:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Sonuçları `dotnet run` görmek için yazın.

## <a name="create-deposits-and-withdrawals"></a>Para yatırma ve çekme işlemleri oluşturun

Banka hesap sınıfınızın doğru çalışması için para yatırma ve para çekme işlemlerini kabul etmesi gerekir. Hesap için her işlemin bir günlüğünü oluşturarak para yatırma ve çekme işlemlerini uygulayalım. Bu sadece her işlem üzerinde bakiyegüncelleme üzerinde birkaç avantajı vardır. Geçmiş, tüm hareketleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir. Gerektiğinde tüm hareketlerin geçmişinden gelen bakiye hesaplandığında, sabit olan tek bir işlemdeki hatalar bir sonraki hesaplamadaki bakiyeye doğru şekilde yansıtılır.

Bir hareketi temsil edecek yeni bir tür oluşturarak başlayalım. Bu herhangi bir sorumluluk yok basit bir türüdür. Birkaç özelliğe ihtiyacı var. *Transaction.cs*adlı yeni bir dosya oluşturun. Buna aşağıdaki kodu ekleyin:

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

Şimdi, `BankAccount` sınıfa bir <xref:System.Collections.Generic.List%601> `Transaction` nesne ekleyelim. Aşağıdaki bildirimi ekleyin:

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

Sınıf, <xref:System.Collections.Generic.List%601> farklı bir ad alanı almanızı gerektirir. *BankAccount.cs*başında aşağıdakileri ekleyin:

```csharp
using System.Collections.Generic;
```

Şimdi, rapor `Balance` edilenin şeklini değiştirelim.  Tüm hareketlerin değerlerini özetleyerek bulunabilir. Sınıftaki `BankAccount` bildirimi `Balance` aşağıdaki şekilde değiştirin:

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

Bu örnek, ***özelliklerin***önemli bir yönünü gösterir. Başka bir programcı değeri sorduğunda bakiyeyi hesaplıyorsun. Hesaplamanız tüm hareketleri sıralar ve toplamı geçerli bakiye olarak sağlar.

Sonra, ve `MakeDeposit` `MakeWithdrawal` yöntemleri uygulayın. Bu yöntemler son iki kuralı uygular: başlangıç bakiyesinin pozitif olması ve herhangi bir geri çekilmenin negatif bir denge oluşturmaması gerekir.

Bu ***özel durumlar***kavramını tanıttı. Bir yöntemin çalışmasını başarıyla tamamlayamayacağını belirtmenin standart yolu, bir özel durum atmaktır. Özel durum türü ve onunla ilişkili ileti hatayı açıklar. Burada, `MakeDeposit` depozito miktarı negatif sayılsa, yöntem bir istisna oluşturur. Yöntem, `MakeWithdrawal` para çekme miktarı negatifse veya para çekme işleminin uygulanması negatif bakiyeyle sonuçlanması durumunda bir istisna oluşturur:

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

İfade [`throw`](../../language-reference/keywords/throw.md) bir özel durum **oluşturur.** Geçerli bloğun yürütülmesi sona erer ve denetim `catch` çağrı yığınında bulunan ilk eşleşen bloğa aktarın. Bu kodu daha `catch` sonra sınamak için bir blok eklersiniz.

Oluşturucu, bakiyeyi doğrudan güncelleştirmek yerine ilk hareketi ekleyen bir değişiklik almalıdır. Yöntemi zaten yazdığınız için, `MakeDeposit` yapıcınızdan arayın. Bitmiş yapıcı aşağıdaki gibi görünmelidir:

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType>geçerli tarih ve saati döndüren bir özelliktir. Yönteminize birkaç para yatırma ve para `Main` çekme ekleyerek bunu test edin:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Ardından, negatif bakiyesi olan bir hesap oluşturmaya çalışarak hata koşullarını yakaladığınızı test edin:

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

Özel durumlar atabilecek bir kod bloğunu işaretlemek ve beklediğiniz hataları yakalamak için ifadeleri kullanırsınız. [ `try` `catch` ](../../language-reference/keywords/try-catch.md) Negatif bakiye için özel durum atan kodu sınamak için aynı tekniği kullanabilirsiniz:

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

Dosyayı kaydedin ve denemek için yazın. `dotnet run`

## <a name="challenge---log-all-transactions"></a>Challenge - tüm işlemleri günlük

Bu öğreticiyi bitirmek için, `GetAccountHistory` işlem geçmişi `string` için bir yöntem oluşturabilirsiniz. Bu yöntemi türe `BankAccount` ekleyin:

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dize biçimlendirmek için sınıfı kullanır. Bu öğreticilerde dize biçimlendirme kodunu daha önce gördünüz. Yeni bir `\t`karakter. Bu, çıktıyı biçimlendirmek için bir sekme ekler.

*Program.cs*olarak test etmek için bu satırı ekleyin:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Sonuçları `dotnet run` görmek için yazın.

## <a name="next-steps"></a>Sonraki adımlar

Eğer sıkışmış varsa, [bizim GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)bu öğretici için kaynak görebilirsiniz.

Tebrikler, C# eğitimlerine girişimizi bitirdiniz. Daha fazla bilgi edinmek istiyorsanız, [öğreticilerimizden](../index.md)daha fazlasını deneyin.
