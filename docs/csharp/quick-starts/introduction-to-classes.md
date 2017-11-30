---
title: "Hızlı Başlangıçlar - sınıfları giriş - C# Kılavuzu"
description: "İlk C# programınızı oluşturma ve nesne yönelimli kavramlarını inceleyin"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: ad6e83d427b55482f9615e0083682bdca6c56704
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="introduction-to-classes"></a><span data-ttu-id="b8712-103">Giriş sınıfları</span><span class="sxs-lookup"><span data-stu-id="b8712-103">Introduction to classes</span></span>

<span data-ttu-id="b8712-104">Bu ders, yüklediğiniz varsayılır [.NET Core SDK](http://dot.net/core)ve tercih ettiğiniz bir düzenleyicide.</span><span class="sxs-lookup"><span data-stu-id="b8712-104">This lesson assumes that you've installed [.NET Core SDK](http://dot.net/core), and an editor of your choice.</span></span> <span data-ttu-id="b8712-105">Yoksa, deneyin [Visual Studio Code](https://code.visualstudio.com/), veya [Visual Studio](https://www.visualstudio.com/) Mac veya Windows.</span><span class="sxs-lookup"><span data-stu-id="b8712-105">If you don't have one, try [Visual Studio Code](https://code.visualstudio.com/), or [Visual Studio](https://www.visualstudio.com/) on Mac or Windows.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="b8712-106">Uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="b8712-106">Create your application</span></span>

<span data-ttu-id="b8712-107">Bir terminal penceresi kullanarak adlı bir dizin oluşturun **sınıfları**.</span><span class="sxs-lookup"><span data-stu-id="b8712-107">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="b8712-108">Uygulamanızı var. oluşturmanız.</span><span class="sxs-lookup"><span data-stu-id="b8712-108">You'll build your application there.</span></span> <span data-ttu-id="b8712-109">Bu dizin ve türünü değiştirme `dotnet new console` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="b8712-109">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="b8712-110">Bu komut, uygulamanızın oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8712-110">This command creates your application.</span></span> <span data-ttu-id="b8712-111">Açık **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="b8712-111">Open **Program.cs**.</span></span> <span data-ttu-id="b8712-112">Aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="b8712-112">It should look like this:</span></span>

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

<span data-ttu-id="b8712-113">Bu Hızlı Başlangıç, banka hesabı temsil eden yeni türlerin oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="b8712-113">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="b8712-114">Genellikle geliştiriciler, farklı bir metin dosyasında her sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8712-114">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="b8712-115">Bu, bir program boyutu büyüdükçe yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b8712-115">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="b8712-116">Adlı yeni bir dosya oluşturun **BankAccount.cs** içinde **sınıfları** dizin.</span><span class="sxs-lookup"><span data-stu-id="b8712-116">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="b8712-117">Bu dosya, deefinition içerecek bir ***banka hesabı***.</span><span class="sxs-lookup"><span data-stu-id="b8712-117">This file will contain the deefinition of a ***bank account***.</span></span> <span data-ttu-id="b8712-118">Oriented programlama kodu biçiminde türleri oluşturarak düzenler nesne ***sınıfları***.</span><span class="sxs-lookup"><span data-stu-id="b8712-118">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="b8712-119">Bu sınıfları, belirli bir varlık gösteren kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="b8712-119">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="b8712-120">`BankAccount` Sınıfı, bir banka hesabı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8712-120">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="b8712-121">Kod yöntemleri ve özellikleri aracılığıyla belirli işlemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="b8712-121">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="b8712-122">Bu Hızlı Başlangıç, banka hesabı bu davranış destekler:</span><span class="sxs-lookup"><span data-stu-id="b8712-122">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="b8712-123">Banka hesabı benzersiz olarak tanıtan 10 basamaklı bir sayı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b8712-123">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="b8712-124">Ad veya adlar sahiplerinin depolayan bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b8712-124">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="b8712-125">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="b8712-125">The balance can be retrieved.</span></span>
1. <span data-ttu-id="b8712-126">Bu, mevduatları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b8712-126">It accepts deposits.</span></span>
1. <span data-ttu-id="b8712-127">Bu, çekilen paralar kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b8712-127">It accepts withdrawals.</span></span>
1. <span data-ttu-id="b8712-128">İlk Bakiye pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-128">The initial balance must be positive.</span></span>
1. <span data-ttu-id="b8712-129">Çekilen paralar bakiyesi negatif olamaz.</span><span class="sxs-lookup"><span data-stu-id="b8712-129">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="b8712-130">Banka hesabı türünü tanımlayın</span><span class="sxs-lookup"><span data-stu-id="b8712-130">Define the bank account type</span></span>

<span data-ttu-id="b8712-131">Bu davranışı tanımlayan bir sınıf temelleri oluşturarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8712-131">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="b8712-132">Şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="b8712-132">It would look like this:</span></span>

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

        public void MakeWithdrawal(decimal amount, DateTime date, string payee, string note)
        {
        }
    }
}
```

<span data-ttu-id="b8712-133">Geçmeden önce temel aldık bir bakalım.</span><span class="sxs-lookup"><span data-stu-id="b8712-133">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="b8712-134">`namespace` Bildirimi kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8712-134">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="b8712-135">Bir ad alanındaki tüm kod gireceğiniz şekilde bu hızlı başlangıç göreceli olarak azdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-135">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="b8712-136">`public class BankAccount`sınıf veya türünü tanımlar oluşturmakta olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="b8712-136">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="b8712-137">İçindeki tüm öğeler `{` ve `}` sınıfı izleyen bildirimi sınıfı davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8712-137">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="b8712-138">Beş vardır ***üyeleri*** , `BankAccount` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8712-138">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="b8712-139">İlk üç olan ***özellikleri***.</span><span class="sxs-lookup"><span data-stu-id="b8712-139">The first three are ***properties***.</span></span> <span data-ttu-id="b8712-140">Özellikler veri öğeleri ve doğrulama veya diğer kurallar zorlar kodu olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8712-140">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="b8712-141">Son iki olan ***yöntemleri***.</span><span class="sxs-lookup"><span data-stu-id="b8712-141">The last two are ***methods***.</span></span> <span data-ttu-id="b8712-142">Yöntemleri bu SPN'i tek bir işlev kodu taşlarıdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-142">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="b8712-143">Her bir üyesinden adlarını okuma yeterli bilgi veya sınıfı ne yapacağını anlamak için başka bir geliştirici sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-143">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="b8712-144">Yeni bir hesap açın</span><span class="sxs-lookup"><span data-stu-id="b8712-144">Open a new account</span></span>

<span data-ttu-id="b8712-145">Uygulanacak ilk banka hesabı açmak için özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="b8712-145">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="b8712-146">Bir müşteri bir hesap oturum açtığında, bir Başlangıç bakiyesi ve sahibi ya da bu hesabı sahipleri hakkında bilgi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8712-146">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="b8712-147">Yeni bir nesne oluşturma `BankAccount` türü anlamına gelir tanımlayan bir ***Oluşturucusu*** bu değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="b8712-147">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="b8712-148">A ***Oluşturucusu*** sınıf ile aynı ada sahip bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="b8712-148">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="b8712-149">Bu sınıf türü nesnelerin başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8712-149">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="b8712-150">Aşağıdaki oluşturucuyu ekleyin `BankAccount` türü:</span><span class="sxs-lookup"><span data-stu-id="b8712-150">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="b8712-151">Kullanarak bir nesne oluşturduğunuz zaman oluşturucular çağrılır [ `new` ](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="b8712-151">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="b8712-152">Satır Değiştir `Console.WriteLine("Hello World!");` içinde ***program.cs*** aşağıdaki satırı ile (Değiştir `<name>` adıyla):</span><span class="sxs-lookup"><span data-stu-id="b8712-152">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="b8712-153">Tür `dotnet run` ne olacağını görmek için.</span><span class="sxs-lookup"><span data-stu-id="b8712-153">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="b8712-154">Hesap numarası boş olduğunu fark ettiniz mi?</span><span class="sxs-lookup"><span data-stu-id="b8712-154">Did you notice that the account number is blank?</span></span> <span data-ttu-id="b8712-155">Bu düzeltme için zaman yapılır.</span><span class="sxs-lookup"><span data-stu-id="b8712-155">It's time to fix that.</span></span> <span data-ttu-id="b8712-156">Nesne oluşturulduğunda hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-156">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="b8712-157">Ancak oluşturmak için arayan sorumluluğunda olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-157">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="b8712-158">`BankAccount` Sınıf kodu yeni hesap numaraları atama hakkında bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="b8712-158">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="b8712-159">Bunu yapmak için basit bir yol ile 10 basamaklı bir sayı başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="b8712-159">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="b8712-160">Her yeni hesap oluşturulduğunda artırın.</span><span class="sxs-lookup"><span data-stu-id="b8712-160">Increment it when each new account is created.</span></span> <span data-ttu-id="b8712-161">Son olarak, bir nesne oluşturulduğunda geçerli hesap numarası depolar.</span><span class="sxs-lookup"><span data-stu-id="b8712-161">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="b8712-162">Aşağıdaki üye bildirimi ekleyin `BankAccount` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b8712-162">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="b8712-163">Bir veri üyesi budur.</span><span class="sxs-lookup"><span data-stu-id="b8712-163">This is a data member.</span></span> <span data-ttu-id="b8712-164">Bunun `private`, yani yalnızca içinde kod tarafından erişilebilmesini `BankAccount` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8712-164">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="b8712-165">Bu (hesap numarası sahip gibi) genel Sorumluluklar (hesap numaralarının nasıl oluşturulduğunu.) özel uygulamasından ayırma bir yoludur Oluşturucuya hesap numarası atamak için aşağıdaki iki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8712-165">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="b8712-166">Tür `dotnet run` sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b8712-166">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="b8712-167">Mevduatlarını ve çekilen paralar oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8712-167">Create deposits and withdrawals</span></span>

<span data-ttu-id="b8712-168">Banka hesabı sınıfınız mevduatlarını ve düzgün çalışması için çekilen paralar kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8712-168">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="b8712-169">Şimdi mevduatlarını ve çekilen paralar her işlem hesabı için bir günlük oluşturarak uygular.</span><span class="sxs-lookup"><span data-stu-id="b8712-169">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="b8712-170">Bu yalnızca her bir işlem bakiyesi güncelleştirilmesi birkaç avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="b8712-170">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="b8712-171">Geçmiş, tüm işlemler denetim ve günlük bakiyelerini yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8712-171">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="b8712-172">Gerektiğinde tüm işlemleri geçmişi Bakiye bilgi işlem tarafından düzeltilen hataları tek bir işlemde doğru bakiyeye üzerinde sonraki hesaplama yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="b8712-172">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="b8712-173">Bir işlem temsil etmek için yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="b8712-173">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="b8712-174">Bu herhangi sorumlulukları sahip olmayan basit bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="b8712-174">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="b8712-175">Birkaç özelliği gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8712-175">It needs a few properties.</span></span> <span data-ttu-id="b8712-176">Adlı yeni bir dosya oluşturun ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="b8712-176">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="b8712-177">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8712-177">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="b8712-178">Şimdi, ekleyelim bir <xref:System.Collections.Generic.List%601> , `Transaction` nesneleri `BankAccount` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8712-178">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="b8712-179">Aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8712-179">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="b8712-180"><xref:System.Collections.Generic.List%601> Sınıfı farklı bir ad alanı almanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b8712-180">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="b8712-181">Aşağıdaki başında ekleyin **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="b8712-181">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="b8712-182">Şimdi, değiştirelim nasıl `Balance` bildirilir.</span><span class="sxs-lookup"><span data-stu-id="b8712-182">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="b8712-183">Tüm işlemleri değerlerini toplayarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b8712-183">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="b8712-184">Bildirimi değiştirme `Balance` içinde `BankAccount` şu sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b8712-184">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="b8712-185">Bu örnek, önemli bir yönü gösterir ***özellikleri***.</span><span class="sxs-lookup"><span data-stu-id="b8712-185">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="b8712-186">Başka bir programcı değeri sorduğunda Bakiye şimdi bilgi işlem.</span><span class="sxs-lookup"><span data-stu-id="b8712-186">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="b8712-187">Hesaplama tüm işlemleri numaralandırır ve toplam olarak geçerli bakiye sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8712-187">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="b8712-188">Ardından, uygulama `MakeDeposit` ve `MakeWithdrawal` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b8712-188">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="b8712-189">Bu yöntemler son iki kural zorunlu kılacak: ilk Bakiye pozitif olmalıdır ve tüm mevzuatı bakiyesi negatif oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8712-189">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="b8712-190">Bu kavramı tanıtır ***özel durumları***.</span><span class="sxs-lookup"><span data-stu-id="b8712-190">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="b8712-191">Bir yöntem çalışmasını başarıyla tamamlanamıyor belirten standart bir özel durum için yoludur.</span><span class="sxs-lookup"><span data-stu-id="b8712-191">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="b8712-192">Özel durum ve onunla ilişkili ileti türünü hata açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8712-192">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="b8712-193">Burada, `MakeDeposit` yöntemi, banka miktarını negatifse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8712-193">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="b8712-194">`MakeWithdrawal` Yöntemi mevzuatı tutar negatifse veya mevzuatı uygulama bakiyesi negatif sonuçlanırsa bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b8712-194">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="b8712-195">[ `throw` ](../language-reference/keywords/throw.md) Deyimi **oluşturur** bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="b8712-195">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="b8712-196">Geçerli yönteminin yürütülmesi sona erer ve eşleşen devam edecek `catch` blok bulundu.</span><span class="sxs-lookup"><span data-stu-id="b8712-196">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="b8712-197">Ekleyeceksiniz bir `catch` bu kodu biraz daha sonra test etmek için blok.</span><span class="sxs-lookup"><span data-stu-id="b8712-197">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="b8712-198">Böylece Bakiye doğrudan güncelleştirme yerine ilk işlem ekler Oluşturucusu bir değişiklik almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8712-198">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="b8712-199">Zaten yazdığınız beri `MakeDeposit` yöntemi, oluşturucudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="b8712-199">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="b8712-200">Tamamlanmış oluşturucusu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="b8712-200">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="b8712-201"><xref:System.DateTime.Now?displayProperty=nameWithType>Geçerli tarih ve saati döndürür bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b8712-201"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="b8712-202">Birkaç mevduatlarını ve içinde çekilen paralar ekleyerek bu test, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b8712-202">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="b8712-203">Ardından, bakiyesi negatif olan bir hesap oluşturulmaya çalışılırken tarafından hata koşulları yakalama test edin:</span><span class="sxs-lookup"><span data-stu-id="b8712-203">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

```csharp
// Test that the initial balances must be positive:
try {
    var invalidAccount = new BankAccount("invalid", -55);
} catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="b8712-204">Kullandığınız [ `try` ve `catch` deyimleri](../language-reference/keywords/try-catch.md) özel durumlar atabilir kod bloğunu işaretlemek için ve beklediğiniz bu hataları yakalamak için.</span><span class="sxs-lookup"><span data-stu-id="b8712-204">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="b8712-205">İçin negatif bir denge oluşturur kodu test etmek için aynı yöntemi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b8712-205">You can use the same technique to test the code that throws for a negative balance:</span></span>

```csharp
// Test for a negative balance
try {
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
} catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="b8712-206">Dosyayı kaydedip türü `dotnet run` denemek üzere.</span><span class="sxs-lookup"><span data-stu-id="b8712-206">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="b8712-207">Sınama - tüm işlemleri günlüğe</span><span class="sxs-lookup"><span data-stu-id="b8712-207">Challenge - log all transactions</span></span>

<span data-ttu-id="b8712-208">Bu hızlı başlangıç tamamlamak için yazabilirsiniz `GetAccountHistory` oluşturan yöntemi bir `string` işlem geçmişi için.</span><span class="sxs-lookup"><span data-stu-id="b8712-208">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="b8712-209">Bu yönteme eklemek `BankAccount` türü:</span><span class="sxs-lookup"><span data-stu-id="b8712-209">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="b8712-210">Bu kullanır <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dize biçimlendirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b8712-210">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="b8712-211">Bu hızlı başlangıçlar önceki kodda biçimlendirme dizesi gördünüz.</span><span class="sxs-lookup"><span data-stu-id="b8712-211">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="b8712-212">Yeni bir karakter `\t`.</span><span class="sxs-lookup"><span data-stu-id="b8712-212">One new character is `\t`.</span></span> <span data-ttu-id="b8712-213">Bu çıktı biçimlendirmek için bir sekmesi ekler.</span><span class="sxs-lookup"><span data-stu-id="b8712-213">That inserts a tab to format the output.</span></span>

<span data-ttu-id="b8712-214">Bunu test etmek için bu satırı ekleyin **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="b8712-214">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="b8712-215">Tür `dotnet run` sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b8712-215">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8712-216">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b8712-216">Next Steps</span></span>

<span data-ttu-id="b8712-217">Takılmış, bu hızlı başlangıç kaynağı görebilirsiniz [bizim GitHub depodaki](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="b8712-217">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="b8712-218">Tebrikler, tüm bizim hızlı başlangıç işlemini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="b8712-218">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="b8712-219">Daha fazla bilgi gezinebileceğinizi, deneyin bizim [öğreticileri](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="b8712-219">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
