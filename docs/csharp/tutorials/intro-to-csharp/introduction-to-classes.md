---
title: Sınıflar ve nesneler- C# öğreticiye giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları gezin
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 5715124a307c7b7fe41b584df82dd328c873ae29
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240086"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="87b52-103">Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet</span><span class="sxs-lookup"><span data-stu-id="87b52-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="87b52-104">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="87b52-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="87b52-105">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="87b52-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="87b52-106">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="87b52-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="87b52-107">Uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="87b52-107">Create your application</span></span>

<span data-ttu-id="87b52-108">Bir Terminal penceresi kullanarak, *sınıflar*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87b52-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="87b52-109">Uygulamanızı burada oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="87b52-109">You'll build your application there.</span></span> <span data-ttu-id="87b52-110">Bu dizine geçin ve konsol penceresinde `dotnet new console` yazın.</span><span class="sxs-lookup"><span data-stu-id="87b52-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="87b52-111">Bu komut uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b52-111">This command creates your application.</span></span> <span data-ttu-id="87b52-112">*Program.cs*'i açın.</span><span class="sxs-lookup"><span data-stu-id="87b52-112">Open *Program.cs*.</span></span> <span data-ttu-id="87b52-113">Şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="87b52-113">It should look like this:</span></span>

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

<span data-ttu-id="87b52-114">Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="87b52-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="87b52-115">Genellikle geliştiriciler her bir sınıfı farklı bir metin dosyasında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87b52-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="87b52-116">Bu, bir program boyutunun büyüdükçe daha kolay yönetilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="87b52-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="87b52-117">*Classes* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87b52-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span> 

<span data-ttu-id="87b52-118">Bu dosya, bir ***Banka hesabının***tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="87b52-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="87b52-119">Nesne odaklı programlama, ***sınıf***biçiminde türler oluşturarak kodu düzenler.</span><span class="sxs-lookup"><span data-stu-id="87b52-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="87b52-120">Bu sınıflar, belirli bir varlığı temsil eden kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="87b52-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="87b52-121">`BankAccount` sınıfı bir banka hesabını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="87b52-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="87b52-122">Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="87b52-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="87b52-123">Bu öğreticide, banka hesabı bu davranışı destekler:</span><span class="sxs-lookup"><span data-stu-id="87b52-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="87b52-124">Bu, banka hesabını benzersiz bir şekilde tanımlayan 10 basamaklı bir sayı içerir.</span><span class="sxs-lookup"><span data-stu-id="87b52-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="87b52-125">Sahiplerinin adını veya adlarını depolayan bir dizesi vardır.</span><span class="sxs-lookup"><span data-stu-id="87b52-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="87b52-126">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="87b52-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="87b52-127">Mevduat kabul eder.</span><span class="sxs-lookup"><span data-stu-id="87b52-127">It accepts deposits.</span></span>
1. <span data-ttu-id="87b52-128">Çekme kabul eder.</span><span class="sxs-lookup"><span data-stu-id="87b52-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="87b52-129">İlk bakiye pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87b52-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="87b52-130">Çekme işlemleri negatif bir bakiyeye neden olamaz.</span><span class="sxs-lookup"><span data-stu-id="87b52-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="87b52-131">Banka hesap türünü tanımlayın</span><span class="sxs-lookup"><span data-stu-id="87b52-131">Define the bank account type</span></span>

<span data-ttu-id="87b52-132">Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b52-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="87b52-133">Şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="87b52-133">It would look like this:</span></span>

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

<span data-ttu-id="87b52-134">Başlamadan önce, derleydiklerinize göz atalım.</span><span class="sxs-lookup"><span data-stu-id="87b52-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="87b52-135">`namespace` bildirimi, kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="87b52-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="87b52-136">Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b52-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="87b52-137">`public class BankAccount` oluşturduğunuz sınıfı veya türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87b52-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="87b52-138">Sınıf bildirimini izleyen `{` ve `}` içindeki her şey, sınıfının durumunu ve davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87b52-138">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="87b52-139">`BankAccount` sınıfının beş ***üyesi*** vardır.</span><span class="sxs-lookup"><span data-stu-id="87b52-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="87b52-140">İlk üçü ***özelliklerdir***.</span><span class="sxs-lookup"><span data-stu-id="87b52-140">The first three are ***properties***.</span></span> <span data-ttu-id="87b52-141">Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="87b52-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="87b52-142">Son ikisi ***metodlardır***.</span><span class="sxs-lookup"><span data-stu-id="87b52-142">The last two are ***methods***.</span></span> <span data-ttu-id="87b52-143">Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="87b52-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="87b52-144">Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="87b52-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="87b52-145">Yeni bir hesap açın</span><span class="sxs-lookup"><span data-stu-id="87b52-145">Open a new account</span></span>

<span data-ttu-id="87b52-146">Uygulanacak ilk özellik bir banka hesabı açmak.</span><span class="sxs-lookup"><span data-stu-id="87b52-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="87b52-147">Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="87b52-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="87b52-148">`BankAccount` türünde yeni bir nesne oluşturmak, bu değerleri atayan bir ***oluşturucunun*** tanımlanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87b52-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="87b52-149">***Oluşturucu*** , sınıfıyla aynı ada sahip olan bir üyedir.</span><span class="sxs-lookup"><span data-stu-id="87b52-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="87b52-150">Bu sınıf türündeki nesneleri başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87b52-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="87b52-151">`BankAccount` türüne aşağıdaki oluşturucuyu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="87b52-152">Oluşturucular, [`new`](../../language-reference/operators/new-operator.md)kullanarak bir nesne oluşturduğunuzda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="87b52-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="87b52-153">*Program.cs* içindeki satır `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin (`<name>` adını adınızla değiştirin):</span><span class="sxs-lookup"><span data-stu-id="87b52-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="87b52-154">Ne olacağını görmek için `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="87b52-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="87b52-155">Hesap numarasının boş olduğunu fark muydunuz?</span><span class="sxs-lookup"><span data-stu-id="87b52-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="87b52-156">Bunun düzeltilmesi zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="87b52-156">It's time to fix that.</span></span> <span data-ttu-id="87b52-157">Nesne oluşturulduğunda hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87b52-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="87b52-158">Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b52-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="87b52-159">`BankAccount` sınıfı kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="87b52-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="87b52-160">Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır.</span><span class="sxs-lookup"><span data-stu-id="87b52-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="87b52-161">Her yeni hesap oluşturulduğunda bunu artırın.</span><span class="sxs-lookup"><span data-stu-id="87b52-161">Increment it when each new account is created.</span></span> <span data-ttu-id="87b52-162">Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.</span><span class="sxs-lookup"><span data-stu-id="87b52-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="87b52-163">`BankAccount` sınıfına aşağıdaki üye bildirimini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="87b52-164">Bu bir veri üyesidir.</span><span class="sxs-lookup"><span data-stu-id="87b52-164">This is a data member.</span></span> <span data-ttu-id="87b52-165">`private`, bu, yalnızca `BankAccount` sınıfının içindeki kodla erişilebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87b52-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="87b52-166">Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="87b52-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="87b52-167">Ayrıca `static`, bu, tüm `BankAccount` nesneleri tarafından paylaşıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87b52-167">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="87b52-168">Statik olmayan bir değişkenin değeri, `BankAccount` nesnesinin her bir örneği için benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="87b52-168">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="87b52-169">Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-169">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="87b52-170">Sonuçları görmek için `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="87b52-170">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="87b52-171">Mevdular ve çekme işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="87b52-171">Create deposits and withdrawals</span></span>

<span data-ttu-id="87b52-172">Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b52-172">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="87b52-173">Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim.</span><span class="sxs-lookup"><span data-stu-id="87b52-173">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="87b52-174">Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="87b52-174">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="87b52-175">Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87b52-175">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="87b52-176">Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="87b52-176">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="87b52-177">Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="87b52-177">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="87b52-178">Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür.</span><span class="sxs-lookup"><span data-stu-id="87b52-178">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="87b52-179">Birkaç özelliğe ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="87b52-179">It needs a few properties.</span></span> <span data-ttu-id="87b52-180">*Transaction.cs*adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87b52-180">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="87b52-181">Buna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-181">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="87b52-182">Şimdi, `BankAccount` sınıfına `Transaction` nesnelerinin <xref:System.Collections.Generic.List%601> ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="87b52-182">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="87b52-183">Aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-183">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="87b52-184"><xref:System.Collections.Generic.List%601> sınıfı, farklı bir ad alanını içeri aktarmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="87b52-184">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="87b52-185">*BankAccount.cs*'nin başlangıcına şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-185">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="87b52-186">Şimdi `Balance` raporlanmasını değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="87b52-186">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="87b52-187">Bu, tüm işlemlerin değerlerini toplayarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="87b52-187">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="87b52-188">`BankAccount` sınıfındaki `Balance` bildirimini aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="87b52-188">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="87b52-189">Bu örnekte, ***özelliklerin***önemli bir yönü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="87b52-189">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="87b52-190">Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="87b52-190">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="87b52-191">Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.</span><span class="sxs-lookup"><span data-stu-id="87b52-191">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="87b52-192">Sonra, `MakeDeposit` ve `MakeWithdrawal` yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="87b52-192">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="87b52-193">Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="87b52-193">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="87b52-194">Bu, ***özel durum***kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="87b52-194">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="87b52-195">Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="87b52-195">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="87b52-196">Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87b52-196">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="87b52-197">Burada, depozito miktarı negatifse `MakeDeposit` yöntemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b52-197">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="87b52-198">`MakeWithdrawal` yöntemi, çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="87b52-198">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="87b52-199">[`throw`](../../language-reference/keywords/throw.md) deyimleri bir özel durum **oluşturur** .</span><span class="sxs-lookup"><span data-stu-id="87b52-199">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="87b52-200">Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen `catch` bloğuna denetim aktarımları yapılır.</span><span class="sxs-lookup"><span data-stu-id="87b52-200">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="87b52-201">Daha sonra bu kodu test etmek için bir `catch` bloğu ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="87b52-201">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="87b52-202">Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b52-202">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="87b52-203">`MakeDeposit` yöntemini zaten yazmış olduğunuz için oluşturucudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="87b52-203">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="87b52-204">Tamamlanmış Oluşturucu şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="87b52-204">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="87b52-205"><xref:System.DateTime.Now?displayProperty=nameWithType>, geçerli tarih ve saati döndüren bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="87b52-205"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="87b52-206">`Main` yönteyinizdeki birkaç mevdua ve çekme bilgilerini ekleyerek bunu test edin:</span><span class="sxs-lookup"><span data-stu-id="87b52-206">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="87b52-207">Daha sonra, negatif bakiyeyle bir hesap oluşturmayı deneyerek hata koşullarını yakalama konusunda test edin:</span><span class="sxs-lookup"><span data-stu-id="87b52-207">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="87b52-208">Özel durum oluşturabilecek bir kod bloğunu işaretlemek ve istediğiniz hataları yakalamak için [`try` ve `catch` deyimlerini](../../language-reference/keywords/try-catch.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b52-208">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="87b52-209">Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87b52-209">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

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

<span data-ttu-id="87b52-210">Dosyayı kaydedin ve denemek için `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="87b52-210">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="87b52-211">Sınama-tüm işlemleri günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="87b52-211">Challenge - log all transactions</span></span>

<span data-ttu-id="87b52-212">Bu öğreticiyi bitirebilmeniz için, işlem geçmişi için bir `string` oluşturan `GetAccountHistory` yöntemi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b52-212">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="87b52-213">Bu yöntemi `BankAccount` türüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-213">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="87b52-214">Bu, her işlem için bir satır içeren bir dizeyi biçimlendirmek için <xref:System.Text.StringBuilder> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="87b52-214">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="87b52-215">Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz.</span><span class="sxs-lookup"><span data-stu-id="87b52-215">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="87b52-216">Yeni bir karakter `\t`.</span><span class="sxs-lookup"><span data-stu-id="87b52-216">One new character is `\t`.</span></span> <span data-ttu-id="87b52-217">Bu, çıktıyı biçimlendirmek için bir sekme ekler.</span><span class="sxs-lookup"><span data-stu-id="87b52-217">That inserts a tab to format the output.</span></span>

<span data-ttu-id="87b52-218">*Program.cs*içinde test etmek için bu satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87b52-218">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="87b52-219">Sonuçları görmek için `dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="87b52-219">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="87b52-220">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="87b52-220">Next steps</span></span>

<span data-ttu-id="87b52-221">Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)deponuzda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b52-221">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="87b52-222">Tebrikler, C# öğreticilere giriş yaptığımızı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="87b52-222">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="87b52-223">Daha fazla bilgi edinmek istiyorsanız [öğreticilerimizi](../index.md)deneyin.</span><span class="sxs-lookup"><span data-stu-id="87b52-223">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
