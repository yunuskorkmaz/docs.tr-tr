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
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="2f38d-103">Sınıflar ve nesnelerle nesne yönelimli programlamayı keşfedin</span><span class="sxs-lookup"><span data-stu-id="2f38d-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="2f38d-104">Bu öğretici, geliştirme için kullanabileceğiniz bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="2f38d-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="2f38d-105">.NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="2f38d-106">Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md) dır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="2f38d-107">Uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="2f38d-107">Create your application</span></span>

<span data-ttu-id="2f38d-108">Terminal pencereyi kullanarak, *sınıflar*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2f38d-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="2f38d-109">Başvurunuzu orada oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2f38d-109">You'll build your application there.</span></span> <span data-ttu-id="2f38d-110">Bu dizini değiştirin `dotnet new console` ve konsol penceresine yazın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="2f38d-111">Bu komut uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f38d-111">This command creates your application.</span></span> <span data-ttu-id="2f38d-112">Açık *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f38d-112">Open *Program.cs*.</span></span> <span data-ttu-id="2f38d-113">Şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="2f38d-113">It should look like this:</span></span>

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

<span data-ttu-id="2f38d-114">Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2f38d-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="2f38d-115">Genellikle geliştiriciler her sınıfı farklı bir metin dosyasında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f38d-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="2f38d-116">Bu, bir programın boyutu arttıkça yönetimi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="2f38d-117">*Sınıflar* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2f38d-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="2f38d-118">Bu dosya bir banka ***hesabının***tanımını içerecektir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="2f38d-119">Nesne Yönelimli programlama ***sınıflar***şeklinde türleri oluşturarak kodu düzenler.</span><span class="sxs-lookup"><span data-stu-id="2f38d-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="2f38d-120">Bu sınıflar belirli bir varlığı temsil eden kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="2f38d-121">Sınıf `BankAccount` bir banka hesabını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f38d-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="2f38d-122">Kod, yöntemler ve özellikler aracılığıyla belirli işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="2f38d-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="2f38d-123">Bu öğreticide, banka hesabı bu davranışı destekler:</span><span class="sxs-lookup"><span data-stu-id="2f38d-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="2f38d-124">Banka hesabını benzersiz olarak tanımlayan 10 basamaklı bir numarası vardır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="2f38d-125">Sahiplerinin adlarını veya adlarını depolayan bir dize vardır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="2f38d-126">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="2f38d-127">Depozito kabul ediyor.</span><span class="sxs-lookup"><span data-stu-id="2f38d-127">It accepts deposits.</span></span>
1. <span data-ttu-id="2f38d-128">Para çekmeyi kabul ediyor.</span><span class="sxs-lookup"><span data-stu-id="2f38d-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="2f38d-129">İlk denge pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="2f38d-130">Para çekme işlemi negatif bir denge yle sonuçlanamaz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="2f38d-131">Banka hesap türünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="2f38d-131">Define the bank account type</span></span>

<span data-ttu-id="2f38d-132">Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="2f38d-133">Bu gibi görünecek:</span><span class="sxs-lookup"><span data-stu-id="2f38d-133">It would look like this:</span></span>

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

<span data-ttu-id="2f38d-134">Devam etmeden önce, ne inşa ettiğinize bir göz atalım.</span><span class="sxs-lookup"><span data-stu-id="2f38d-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="2f38d-135">Bildirim, `namespace` kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f38d-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="2f38d-136">Bu öğretici nispeten küçüktür, bu nedenle tüm kodu tek bir ad alanına koyarsınız.</span><span class="sxs-lookup"><span data-stu-id="2f38d-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="2f38d-137">`public class BankAccount`oluşturduğunuz sınıfı veya türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f38d-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="2f38d-138">Sınıf `{` bildiriminin `}` içindeki ve izleyen her şey sınıfın durumunu ve davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f38d-138">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="2f38d-139">Sınıfın beş üyesi var. ***members*** `BankAccount`</span><span class="sxs-lookup"><span data-stu-id="2f38d-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="2f38d-140">İlk üçü ***özellikleridir.***</span><span class="sxs-lookup"><span data-stu-id="2f38d-140">The first three are ***properties***.</span></span> <span data-ttu-id="2f38d-141">Özellikler veri öğeleridir ve doğrulama yı veya diğer kuralları zorlayan bir koda sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="2f38d-142">Son iki ***yöntem***dir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-142">The last two are ***methods***.</span></span> <span data-ttu-id="2f38d-143">Yöntemler, tek bir işlev icra eden kod bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="2f38d-144">Üyelerin her birinin adlarını okumak, sınıfın ne yaptığını anlamak için sizin veya başka bir geliştiriciiçin yeterli bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="2f38d-145">Yeni bir hesap açma</span><span class="sxs-lookup"><span data-stu-id="2f38d-145">Open a new account</span></span>

<span data-ttu-id="2f38d-146">Uygulanacak ilk özellik bir banka hesabı açmaktır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="2f38d-147">Bir müşteri bir hesap açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="2f38d-148">`BankAccount` Türünden yeni bir nesne oluşturmak, bu değerleri atayan bir ***oluşturucu*** tanımlama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="2f38d-149">***Oluşturucu,*** sınıfla aynı ada sahip bir üyedir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="2f38d-150">Bu sınıf türünesneleri başlatılması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="2f38d-151">Türüne aşağıdaki oluşturucu `BankAccount` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="2f38d-152">Bir nesne oluşturduğunuzda yapıcılar [`new`](../../language-reference/operators/new-operator.md)çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="2f38d-153">`Console.WriteLine("Hello World!");` satırı *Program.cs* aşağıdaki kodla değiştirin `<name>` (adınız ile değiştirin):</span><span class="sxs-lookup"><span data-stu-id="2f38d-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="2f38d-154">Ne `dotnet run` olacağını görmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="2f38d-155">Hesap numarasının boş olduğunu fark ettin mi?</span><span class="sxs-lookup"><span data-stu-id="2f38d-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="2f38d-156">Bunu düzeltmenin zamanı oldu.</span><span class="sxs-lookup"><span data-stu-id="2f38d-156">It's time to fix that.</span></span> <span data-ttu-id="2f38d-157">Nesne oluşturulduğunda hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="2f38d-158">Ama onu oluşturmak arayan kişinin sorumluluğu nda olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="2f38d-159">Sınıf `BankAccount` kodu yeni hesap numaraları atamayı bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="2f38d-160">Bunu yapmanın basit bir yolu 10 basamaklı bir sayı ile başlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="2f38d-161">Her yeni hesap oluşturulduğunda artım.</span><span class="sxs-lookup"><span data-stu-id="2f38d-161">Increment it when each new account is created.</span></span> <span data-ttu-id="2f38d-162">Son olarak, bir nesne oluşturulduğunda cari hesap numarasını depolayın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="2f38d-163">Sınıfa aşağıdaki üye `BankAccount` bildirimini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="2f38d-164">Bu bir veri üyesi.</span><span class="sxs-lookup"><span data-stu-id="2f38d-164">This is a data member.</span></span> <span data-ttu-id="2f38d-165">Yani `private`sadece `BankAccount` sınıf içindeki kodla erişilebiliyor.</span><span class="sxs-lookup"><span data-stu-id="2f38d-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="2f38d-166">Bu, genel sorumlulukları (hesap numarasına sahip olmak gibi) özel uygulamadan (hesap numaralarının nasıl oluşturulduğunu) ayırmanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="2f38d-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="2f38d-167">Aynı zamanda, `static`tüm `BankAccount` nesneler tarafından paylaşılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-167">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="2f38d-168">Statik olmayan bir değişkenin değeri `BankAccount` nesnenin her örneğine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="2f38d-168">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="2f38d-169">Hesap numarasını atamak için aşağıdaki iki satırı oluşturucuya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-169">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="2f38d-170">Sonuçları `dotnet run` görmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-170">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="2f38d-171">Para yatırma ve çekme işlemleri oluşturun</span><span class="sxs-lookup"><span data-stu-id="2f38d-171">Create deposits and withdrawals</span></span>

<span data-ttu-id="2f38d-172">Banka hesap sınıfınızın doğru çalışması için para yatırma ve para çekme işlemlerini kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-172">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="2f38d-173">Hesap için her işlemin bir günlüğünü oluşturarak para yatırma ve çekme işlemlerini uygulayalım.</span><span class="sxs-lookup"><span data-stu-id="2f38d-173">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="2f38d-174">Bu sadece her işlem üzerinde bakiyegüncelleme üzerinde birkaç avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-174">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="2f38d-175">Geçmiş, tüm hareketleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-175">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="2f38d-176">Gerektiğinde tüm hareketlerin geçmişinden gelen bakiye hesaplandığında, sabit olan tek bir işlemdeki hatalar bir sonraki hesaplamadaki bakiyeye doğru şekilde yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-176">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="2f38d-177">Bir hareketi temsil edecek yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="2f38d-177">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="2f38d-178">Bu herhangi bir sorumluluk yok basit bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="2f38d-178">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="2f38d-179">Birkaç özelliğe ihtiyacı var.</span><span class="sxs-lookup"><span data-stu-id="2f38d-179">It needs a few properties.</span></span> <span data-ttu-id="2f38d-180">*Transaction.cs*adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2f38d-180">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="2f38d-181">Buna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-181">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="2f38d-182">Şimdi, `BankAccount` sınıfa bir <xref:System.Collections.Generic.List%601> `Transaction` nesne ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="2f38d-182">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="2f38d-183">Aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-183">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="2f38d-184">Sınıf, <xref:System.Collections.Generic.List%601> farklı bir ad alanı almanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-184">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="2f38d-185">*BankAccount.cs*başında aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-185">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="2f38d-186">Şimdi, rapor `Balance` edilenin şeklini değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="2f38d-186">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="2f38d-187">Tüm hareketlerin değerlerini özetleyerek bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-187">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="2f38d-188">Sınıftaki `BankAccount` bildirimi `Balance` aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-188">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="2f38d-189">Bu örnek, ***özelliklerin***önemli bir yönünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-189">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="2f38d-190">Başka bir programcı değeri sorduğunda bakiyeyi hesaplıyorsun.</span><span class="sxs-lookup"><span data-stu-id="2f38d-190">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="2f38d-191">Hesaplamanız tüm hareketleri sıralar ve toplamı geçerli bakiye olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f38d-191">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="2f38d-192">Sonra, ve `MakeDeposit` `MakeWithdrawal` yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-192">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="2f38d-193">Bu yöntemler son iki kuralı uygular: başlangıç bakiyesinin pozitif olması ve herhangi bir geri çekilmenin negatif bir denge oluşturmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-193">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="2f38d-194">Bu ***özel durumlar***kavramını tanıttı.</span><span class="sxs-lookup"><span data-stu-id="2f38d-194">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="2f38d-195">Bir yöntemin çalışmasını başarıyla tamamlayamayacağını belirtmenin standart yolu, bir özel durum atmaktır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-195">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="2f38d-196">Özel durum türü ve onunla ilişkili ileti hatayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2f38d-196">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="2f38d-197">Burada, `MakeDeposit` depozito miktarı negatif sayılsa, yöntem bir istisna oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f38d-197">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="2f38d-198">Yöntem, `MakeWithdrawal` para çekme miktarı negatifse veya para çekme işleminin uygulanması negatif bakiyeyle sonuçlanması durumunda bir istisna oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2f38d-198">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="2f38d-199">İfade [`throw`](../../language-reference/keywords/throw.md) bir özel durum **oluşturur.**</span><span class="sxs-lookup"><span data-stu-id="2f38d-199">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="2f38d-200">Geçerli bloğun yürütülmesi sona erer ve denetim `catch` çağrı yığınında bulunan ilk eşleşen bloğa aktarın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-200">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="2f38d-201">Bu kodu daha `catch` sonra sınamak için bir blok eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-201">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="2f38d-202">Oluşturucu, bakiyeyi doğrudan güncelleştirmek yerine ilk hareketi ekleyen bir değişiklik almalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-202">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="2f38d-203">Yöntemi zaten yazdığınız için, `MakeDeposit` yapıcınızdan arayın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-203">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="2f38d-204">Bitmiş yapıcı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="2f38d-204">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="2f38d-205"><xref:System.DateTime.Now?displayProperty=nameWithType>geçerli tarih ve saati döndüren bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2f38d-205"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="2f38d-206">Yönteminize birkaç para yatırma ve para `Main` çekme ekleyerek bunu test edin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-206">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="2f38d-207">Ardından, negatif bakiyesi olan bir hesap oluşturmaya çalışarak hata koşullarını yakaladığınızı test edin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-207">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="2f38d-208">Özel durumlar atabilecek bir kod bloğunu işaretlemek ve beklediğiniz hataları yakalamak için ifadeleri kullanırsınız. [ `try` `catch` ](../../language-reference/keywords/try-catch.md)</span><span class="sxs-lookup"><span data-stu-id="2f38d-208">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="2f38d-209">Negatif bakiye için özel durum atan kodu sınamak için aynı tekniği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2f38d-209">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="2f38d-210">Dosyayı kaydedin ve denemek için yazın. `dotnet run`</span><span class="sxs-lookup"><span data-stu-id="2f38d-210">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="2f38d-211">Challenge - tüm işlemleri günlük</span><span class="sxs-lookup"><span data-stu-id="2f38d-211">Challenge - log all transactions</span></span>

<span data-ttu-id="2f38d-212">Bu öğreticiyi bitirmek için, `GetAccountHistory` işlem geçmişi `string` için bir yöntem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-212">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="2f38d-213">Bu yöntemi türe `BankAccount` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-213">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="2f38d-214">Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dize biçimlendirmek için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f38d-214">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="2f38d-215">Bu öğreticilerde dize biçimlendirme kodunu daha önce gördünüz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-215">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="2f38d-216">Yeni bir `\t`karakter.</span><span class="sxs-lookup"><span data-stu-id="2f38d-216">One new character is `\t`.</span></span> <span data-ttu-id="2f38d-217">Bu, çıktıyı biçimlendirmek için bir sekme ekler.</span><span class="sxs-lookup"><span data-stu-id="2f38d-217">That inserts a tab to format the output.</span></span>

<span data-ttu-id="2f38d-218">*Program.cs*olarak test etmek için bu satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f38d-218">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="2f38d-219">Sonuçları `dotnet run` görmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="2f38d-219">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f38d-220">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2f38d-220">Next steps</span></span>

<span data-ttu-id="2f38d-221">Eğer sıkışmış varsa, [bizim GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)bu öğretici için kaynak görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-221">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="2f38d-222">Tebrikler, C# eğitimlerine girişimizi bitirdiniz.</span><span class="sxs-lookup"><span data-stu-id="2f38d-222">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="2f38d-223">Daha fazla bilgi edinmek istiyorsanız, [öğreticilerimizden](../index.md)daha fazlasını deneyin.</span><span class="sxs-lookup"><span data-stu-id="2f38d-223">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
