---
title: Sınıflar ve nesneler - giriş C# Öğreticisi
description: İlk C# programınızı oluşturma ve nesne yönelimli kavramları keşfedin
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 0932ae8a9d3facd4b2a8469664922f163fe4c679
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397818"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="c693e-103">Nesne yönelimli programlama ile ilgili sınıfları ve nesneleri keşfedin</span><span class="sxs-lookup"><span data-stu-id="c693e-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="c693e-104">Bu öğreticide, geliştirme için kullanabileceğiniz bir makine olmasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="c693e-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="c693e-105">.NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="c693e-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="c693e-106">Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="c693e-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="c693e-107">Uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c693e-107">Create your application</span></span>

<span data-ttu-id="c693e-108">Bir terminal penceresinde kullanarak adlı bir dizin oluşturma **sınıfları**.</span><span class="sxs-lookup"><span data-stu-id="c693e-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="c693e-109">Uygulamanız var. oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c693e-109">You'll build your application there.</span></span> <span data-ttu-id="c693e-110">Bu dizin ve türü değiştirme `dotnet new console` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="c693e-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="c693e-111">Bu komut, uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c693e-111">This command creates your application.</span></span> <span data-ttu-id="c693e-112">Açık **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="c693e-112">Open **Program.cs**.</span></span> <span data-ttu-id="c693e-113">Şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c693e-113">It should look like this:</span></span>

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

<span data-ttu-id="c693e-114">Bu öğreticide, bir banka hesabı temsil eden yeni türler oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="c693e-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="c693e-115">Genellikle geliştiriciler, farklı metin dosyasında her sınıfı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c693e-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="c693e-116">Bu, bir program boyutu büyüdükçe yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c693e-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="c693e-117">Adlı yeni bir dosya oluşturun **BankAccount.cs** içinde **sınıfları** dizin.</span><span class="sxs-lookup"><span data-stu-id="c693e-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="c693e-118">Bu dosya tanımını içerecek bir ***banka hesabı***.</span><span class="sxs-lookup"><span data-stu-id="c693e-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="c693e-119">Oriented programlama biçiminde türleri oluşturarak kodu düzenler nesne ***sınıfları***.</span><span class="sxs-lookup"><span data-stu-id="c693e-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="c693e-120">Bu sınıflar, belirli bir varlığı temsil eden kodu bulunur.</span><span class="sxs-lookup"><span data-stu-id="c693e-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="c693e-121">`BankAccount` Sınıfı, bir banka hesabı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c693e-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="c693e-122">Kod, yöntemleri ve özellikleri aracılığıyla belirli işlemler uygular.</span><span class="sxs-lookup"><span data-stu-id="c693e-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="c693e-123">Bu öğreticide, bu davranışı banka hesabı destekler:</span><span class="sxs-lookup"><span data-stu-id="c693e-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="c693e-124">Banka hesabı benzersiz olarak tanımlayan 10 basamaklı bir sayı var.</span><span class="sxs-lookup"><span data-stu-id="c693e-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="c693e-125">Adı veya adları sahiplerinin depolayan bir dize var.</span><span class="sxs-lookup"><span data-stu-id="c693e-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="c693e-126">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="c693e-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="c693e-127">Bu, mevduatları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c693e-127">It accepts deposits.</span></span>
1. <span data-ttu-id="c693e-128">Bunun çekilen paralar kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c693e-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="c693e-129">Başlangıç bakiyesi pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c693e-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="c693e-130">Çekilen paralar negatif bakiyeye sonuçlanmaz.</span><span class="sxs-lookup"><span data-stu-id="c693e-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="c693e-131">Banka hesabı türünü tanımlayın</span><span class="sxs-lookup"><span data-stu-id="c693e-131">Define the bank account type</span></span>

<span data-ttu-id="c693e-132">Bu davranışı tanımlayan bir sınıf temelleri oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c693e-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="c693e-133">Şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="c693e-133">It would look like this:</span></span>

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

<span data-ttu-id="c693e-134">Geçmeden önce şimdi ne derlediğiniz bir göz atalım.</span><span class="sxs-lookup"><span data-stu-id="c693e-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="c693e-135">`namespace` Bildirimi kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c693e-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="c693e-136">Bu öğreticide görece küçük olduğundan bir ad alanındaki tüm kod giriyorum.</span><span class="sxs-lookup"><span data-stu-id="c693e-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="c693e-137">`public class BankAccount` sınıf veya tür, tanımlar oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c693e-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="c693e-138">İçindeki her şey `{` ve `}` , sınıf aşağıdaki bildirimi, sınıf davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c693e-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="c693e-139">Beş vardır ***üyeleri*** , `BankAccount` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c693e-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="c693e-140">İlk üç olan ***özellikleri***.</span><span class="sxs-lookup"><span data-stu-id="c693e-140">The first three are ***properties***.</span></span> <span data-ttu-id="c693e-141">Özellikler veri öğelerini ve doğrulama veya diğer kuralları zorlar kodu oluşturmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c693e-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="c693e-142">Son iki olan ***yöntemleri***.</span><span class="sxs-lookup"><span data-stu-id="c693e-142">The last two are ***methods***.</span></span> <span data-ttu-id="c693e-143">Tek bir işlevi gerçekleştiren kod blokları yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="c693e-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="c693e-144">Her üye adlarını okuma yeterli bilgi veya sınıf ne yaptığını anlamak için başka bir geliştirici sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c693e-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="c693e-145">Yeni hesabı açın</span><span class="sxs-lookup"><span data-stu-id="c693e-145">Open a new account</span></span>

<span data-ttu-id="c693e-146">İlk özellik uygulamak için bir banka hesabı açmaktır.</span><span class="sxs-lookup"><span data-stu-id="c693e-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="c693e-147">Bir müşteri bir hesap oturum açtığında, bir Başlangıç bakiyesi ve sahip veya bu hesap sahipleri hakkında bilgi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c693e-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="c693e-148">Yeni bir nesne oluşturma `BankAccount` türü anlamına gelir tanımlayan bir ***Oluşturucusu*** bu değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="c693e-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="c693e-149">A ***Oluşturucusu*** sınıfı aynı ada sahip bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="c693e-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="c693e-150">Bu sınıf türü nesnelerini başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c693e-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="c693e-151">Aşağıdaki oluşturucuyu ekleyin `BankAccount` türü:</span><span class="sxs-lookup"><span data-stu-id="c693e-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="c693e-152">Oluşturucuları kullanarak bir nesne oluşturduğunuzda çağrılır [ `new` ](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c693e-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="c693e-153">Satırı değiştirin `Console.WriteLine("Hello World!");` içinde ***program.cs*** aşağıdaki satırı ile (Değiştir `<name>` adınızla):</span><span class="sxs-lookup"><span data-stu-id="c693e-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="c693e-154">Tür `dotnet run` ne olacağını görmek için.</span><span class="sxs-lookup"><span data-stu-id="c693e-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="c693e-155">Hesap numarası boş olduğunu fark ettiniz mi?</span><span class="sxs-lookup"><span data-stu-id="c693e-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="c693e-156">Buna, süreyi var.</span><span class="sxs-lookup"><span data-stu-id="c693e-156">It's time to fix that.</span></span> <span data-ttu-id="c693e-157">Nesne oluşturulduğunda, hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c693e-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="c693e-158">Ancak, arayanın oluşturmak için sorumluluk olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c693e-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="c693e-159">`BankAccount` Sınıf kodunu, yeni hesap numaraları atama bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c693e-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="c693e-160">Bunu yapmak için basit bir yol ile 10 basamaklı bir sayı başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="c693e-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="c693e-161">Her yeni bir hesap oluşturulduğunda, artırın.</span><span class="sxs-lookup"><span data-stu-id="c693e-161">Increment it when each new account is created.</span></span> <span data-ttu-id="c693e-162">Son olarak, bir nesne oluşturulduğunda geçerli hesap numarası depolayın.</span><span class="sxs-lookup"><span data-stu-id="c693e-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="c693e-163">Aşağıdaki üye bildirimi için ekleme `BankAccount` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="c693e-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="c693e-164">Bir veri üyesi budur.</span><span class="sxs-lookup"><span data-stu-id="c693e-164">This is a data member.</span></span> <span data-ttu-id="c693e-165">Sahip `private`, yani yalnızca içinde kod tarafından erişilebilir `BankAccount` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c693e-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="c693e-166">(Bir hesap numarası sahip gibi) genel Sorumluluklar (nasıl hesap numaraları oluşturulur.) özel uygulamadan ayırma bir yoludur Ayrıca `static`, yani tüm tarafından paylaşılan `BankAccount` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c693e-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="c693e-167">Statik olmayan bir değişkenin değerini her örneği için benzersiz olan `BankAccount` nesne.</span><span class="sxs-lookup"><span data-stu-id="c693e-167">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="c693e-168">Aşağıdaki iki satırı hesabı atamak için oluşturucuyu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c693e-168">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="c693e-169">Tür `dotnet run` sonuçları görmek için.</span><span class="sxs-lookup"><span data-stu-id="c693e-169">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="c693e-170">Mevduatlarını ve çekilen paralar oluşturma</span><span class="sxs-lookup"><span data-stu-id="c693e-170">Create deposits and withdrawals</span></span>

<span data-ttu-id="c693e-171">Banka hesabı sınıfınıza mevduatlarını ve düzgün çalışması için çekilen paralar kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c693e-171">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="c693e-172">Şimdi mevduatlarını ve çekilen paralar sefer hesabı için bir günlük oluşturarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c693e-172">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="c693e-173">Her işlem bakiyeye güncelleştirerek kolayca bazı avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="c693e-173">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="c693e-174">Geçmiş, tüm işlemler denetim ve günlük bakiyeleri yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c693e-174">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="c693e-175">Gerektiğinde tüm işlemleri geçmişini bakiyeden bilgi işlem tarafından düzeltilen hataları tek bir işlemde doğru dengesi üzerinde sonraki hesaplama yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="c693e-175">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="c693e-176">Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="c693e-176">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="c693e-177">Bu tüm Sorumluluklar sahip olmayan basit bir türdür.</span><span class="sxs-lookup"><span data-stu-id="c693e-177">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="c693e-178">Bunun birkaç özellik gerekir.</span><span class="sxs-lookup"><span data-stu-id="c693e-178">It needs a few properties.</span></span> <span data-ttu-id="c693e-179">Adlı yeni bir dosya oluşturun ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="c693e-179">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="c693e-180">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c693e-180">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="c693e-181">Şimdi, ekleyelim bir <xref:System.Collections.Generic.List%601> , `Transaction` nesneleri için `BankAccount` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c693e-181">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="c693e-182">Aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c693e-182">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="c693e-183"><xref:System.Collections.Generic.List%601> Sınıfı farklı bir ad alanı almanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c693e-183">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="c693e-184">Başında ekleyin **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="c693e-184">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="c693e-185">Şimdi, değiştirelim nasıl `Balance` bildirilir.</span><span class="sxs-lookup"><span data-stu-id="c693e-185">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="c693e-186">Tüm işlemlerin değerleri toplayarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c693e-186">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="c693e-187">Değiştirin `Balance` içinde `BankAccount` aşağıdaki sınıfı:</span><span class="sxs-lookup"><span data-stu-id="c693e-187">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="c693e-188">Bu örnek, önemli bir yönüdür gösterir ***özellikleri***.</span><span class="sxs-lookup"><span data-stu-id="c693e-188">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="c693e-189">Başka bir programcı değeri sorduğunda Bakiye artık bilgi işlem.</span><span class="sxs-lookup"><span data-stu-id="c693e-189">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="c693e-190">Kendi hesaplama tüm işlemleri numaralandırır ve toplam tutar kadar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c693e-190">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="c693e-191">Ardından, uygulama `MakeDeposit` ve `MakeWithdrawal` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c693e-191">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="c693e-192">Son iki kural bu yöntemlerin kullanılmasını zorunlu: Başlangıç bakiyesi pozitif ve negatif bir denge herhangi mevzuatı oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c693e-192">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="c693e-193">Bu kavramı tanıtır ***özel durumları***.</span><span class="sxs-lookup"><span data-stu-id="c693e-193">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="c693e-194">Bir yöntem işini başarıyla tamamlanamıyor belirten standart bir özel durum için yoludur.</span><span class="sxs-lookup"><span data-stu-id="c693e-194">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="c693e-195">Özel durum ve onunla ilişkili ileti türünü hata açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c693e-195">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="c693e-196">Burada, `MakeDeposit` yöntemi havale miktarını negatif ise bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c693e-196">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="c693e-197">`MakeWithdrawal` Mevzuatı tutar negatif ise ya da uygulama mevzuatı negatif bakiyeye sonuçlanırsa yöntemi bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c693e-197">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="c693e-198">[ `throw` ](../../language-reference/keywords/throw.md) Deyimi **oluşturur** bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="c693e-198">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="c693e-199">Geçerli yürütme engelleme sona erer ve denetim ilk eşleştirme aktarımları `catch` blok çağrı yığınında bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="c693e-199">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="c693e-200">Ekleyeceğiniz bir `catch` Bu kod biraz daha sonra test etmek için blok.</span><span class="sxs-lookup"><span data-stu-id="c693e-200">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="c693e-201">Oluşturucu, Bakiye doğrudan güncelleştirmek yerine bir ilk işlem ekler, böylece bir değişiklik almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c693e-201">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="c693e-202">Zaten yazdığınız beri `MakeDeposit` yöntemi, oluşturucudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="c693e-202">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="c693e-203">Tamamlanmış Oluşturucusu gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c693e-203">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="c693e-204"><xref:System.DateTime.Now?displayProperty=nameWithType> Geçerli tarih ve saati döndürür bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c693e-204"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="c693e-205">Birkaç mevduatlarını ve de çekilen paralar ekleyerek bu test, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c693e-205">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="c693e-206">Ardından, negatif bakiyesi olan bir hesap oluşturulmaya çalışılırken tarafından hata koşulları yakalama test edin:</span><span class="sxs-lookup"><span data-stu-id="c693e-206">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="c693e-207">Kullandığınız [ `try` ve `catch` deyimleri](../../language-reference/keywords/try-catch.md) bir özel durum oluşturabildiğini varsaymasını kod bloğu işaretlemek için ve beklediğiniz bu hataları yakalamak için.</span><span class="sxs-lookup"><span data-stu-id="c693e-207">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="c693e-208">Bir negatif dengelemek için bir özel durum kodu test etmek için aynı tekniği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c693e-208">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="c693e-209">Dosya ve tür Kaydet `dotnet run` denemek için.</span><span class="sxs-lookup"><span data-stu-id="c693e-209">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="c693e-210">Sınaması - tüm işlemlerini günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="c693e-210">Challenge - log all transactions</span></span>

<span data-ttu-id="c693e-211">Bu öğreticiyi tamamlamak için şunu yazabilirsiniz `GetAccountHistory` oluşturan yöntemine bir `string` işlem geçmişi.</span><span class="sxs-lookup"><span data-stu-id="c693e-211">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="c693e-212">Bu yönteme ekleme `BankAccount` türü:</span><span class="sxs-lookup"><span data-stu-id="c693e-212">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="c693e-213">Bu kullanır <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c693e-213">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="c693e-214">Bu öğreticileri, kod biçimlendirme dizesi gördünüz.</span><span class="sxs-lookup"><span data-stu-id="c693e-214">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="c693e-215">Yeni bir karakter `\t`.</span><span class="sxs-lookup"><span data-stu-id="c693e-215">One new character is `\t`.</span></span> <span data-ttu-id="c693e-216">Çıktıyı biçimlendirmek için bir sekme ekler.</span><span class="sxs-lookup"><span data-stu-id="c693e-216">That inserts a tab to format the output.</span></span>

<span data-ttu-id="c693e-217">Bunu test etmek için bu satırı ekleyin **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="c693e-217">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="c693e-218">Tür `dotnet run` sonuçları görmek için.</span><span class="sxs-lookup"><span data-stu-id="c693e-218">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c693e-219">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c693e-219">Next Steps</span></span>

<span data-ttu-id="c693e-220">Takılı, Bu öğretici için kaynak görebilirsiniz [GitHub depomuz içinde](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="c693e-220">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="c693e-221">Tebrikler, sunduğumuz tüm giriş bitirdikten C# öğreticiler.</span><span class="sxs-lookup"><span data-stu-id="c693e-221">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="c693e-222">Daha fazla bilgi edinmek için, daha fazlasını deneyin bizim [öğreticiler](../index.md)</span><span class="sxs-lookup"><span data-stu-id="c693e-222">If you're eager to learn more, try more of our [tutorials](../index.md)</span></span>
