---
title: Sınıflar ve nesneler-C# öğreticisine giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları keşfedebilirsiniz
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 0955b0ac33b346b9880c8af70bd73cb458120f35
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434891"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="5f62b-103">Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet</span><span class="sxs-lookup"><span data-stu-id="5f62b-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="5f62b-104">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="5f62b-105">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="5f62b-106">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="5f62b-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="5f62b-107">Uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f62b-107">Create your application</span></span>

<span data-ttu-id="5f62b-108">Bir Terminal penceresi kullanarak, *sınıflar*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f62b-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="5f62b-109">Uygulamanızı burada oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5f62b-109">You'll build your application there.</span></span> <span data-ttu-id="5f62b-110">Bu dizine geçin ve `dotnet new console` konsol penceresinde yazın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="5f62b-111">Bu komut uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f62b-111">This command creates your application.</span></span> <span data-ttu-id="5f62b-112">*Program.cs*'i açın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-112">Open *Program.cs*.</span></span> <span data-ttu-id="5f62b-113">Şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5f62b-113">It should look like this:</span></span>

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

<span data-ttu-id="5f62b-114">Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5f62b-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="5f62b-115">Genellikle geliştiriciler her bir sınıfı farklı bir metin dosyasında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f62b-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="5f62b-116">Bu, bir program boyutunun büyüdükçe daha kolay yönetilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f62b-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="5f62b-117">*Classes* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f62b-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="5f62b-118">Bu dosya, \***Banka hesabı**_ tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-118">This file will contain the definition of a \***bank account**_.</span></span> <span data-ttu-id="5f62b-119">Nesne odaklı programlama, _*_sınıf_*_ biçiminde türler oluşturarak kodu düzenler.</span><span class="sxs-lookup"><span data-stu-id="5f62b-119">Object Oriented programming organizes code by creating types in the form of _*_classes_*_.</span></span> <span data-ttu-id="5f62b-120">Bu sınıflar, belirli bir varlığı temsil eden kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="5f62b-121">`BankAccount`Sınıfı bir banka hesabını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f62b-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="5f62b-122">Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="5f62b-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="5f62b-123">Bu öğreticide, banka hesabı bu davranışı destekler:</span><span class="sxs-lookup"><span data-stu-id="5f62b-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="5f62b-124">Bu, banka hesabını benzersiz bir şekilde tanımlayan 10 basamaklı bir sayı içerir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="5f62b-125">Sahiplerinin adını veya adlarını depolayan bir dizesi vardır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="5f62b-126">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="5f62b-127">Mevduat kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5f62b-127">It accepts deposits.</span></span>
1. <span data-ttu-id="5f62b-128">Çekme kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5f62b-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="5f62b-129">İlk bakiye pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="5f62b-130">Çekme işlemleri negatif bir bakiyeye neden olamaz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="5f62b-131">Banka hesap türünü tanımlayın</span><span class="sxs-lookup"><span data-stu-id="5f62b-131">Define the bank account type</span></span>

<span data-ttu-id="5f62b-132">Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="5f62b-133">_*File: New*\* komutunu kullanarak yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f62b-133">Create a new file using the _*File:New*\* command.</span></span> <span data-ttu-id="5f62b-134">*BankAccount.cs*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="5f62b-135">Aşağıdaki kodu *BankAccount.cs* dosyanıza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="5f62b-136">Başlamadan önce, derleydiklerinize göz atalım.</span><span class="sxs-lookup"><span data-stu-id="5f62b-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="5f62b-137">`namespace`Bildirimi, kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f62b-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="5f62b-138">Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="5f62b-139">`public class BankAccount` oluşturmakta olduğunuz sınıfı veya türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f62b-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="5f62b-140">`{`Sınıf bildirimini izleyen ve içindeki her şey, `}` sınıfının durumunu ve davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f62b-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="5f62b-141">Sınıfın beş \***üyesi**_ `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-141">There are five \***members**_ of the `BankAccount` class.</span></span> <span data-ttu-id="5f62b-142">İlk üçü _\*_özelliklerdir_\*_.</span><span class="sxs-lookup"><span data-stu-id="5f62b-142">The first three are _*_properties_*_.</span></span> <span data-ttu-id="5f62b-143">Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="5f62b-144">Son ikisi _*_metodlardır_*_.</span><span class="sxs-lookup"><span data-stu-id="5f62b-144">The last two are _*_methods_*_.</span></span> <span data-ttu-id="5f62b-145">Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="5f62b-146">Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="5f62b-147">Yeni bir hesap açın</span><span class="sxs-lookup"><span data-stu-id="5f62b-147">Open a new account</span></span>

<span data-ttu-id="5f62b-148">Uygulanacak ilk özellik bir banka hesabı açmak.</span><span class="sxs-lookup"><span data-stu-id="5f62b-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="5f62b-149">Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="5f62b-150">Türünde yeni bir nesne oluşturmak, `BankAccount` Bu değerleri atayan bir _*_Oluşturucu_*_ tanımlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-150">Creating a new object of the `BankAccount` type means defining a _*_constructor_*_ that assigns those values.</span></span> <span data-ttu-id="5f62b-151">_*_Oluşturucu_*_ , sınıfıyla aynı ada sahip olan bir üyedir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-151">A _*_constructor_*_ is a member that has the same name as the class.</span></span> <span data-ttu-id="5f62b-152">Bu sınıf türündeki nesneleri başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="5f62b-153">Türe aşağıdaki oluşturucuyu ekleyin `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="5f62b-154">Aşağıdaki kodu bildiriminin üzerine yerleştirin `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="5f62b-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="5f62b-155">Oluşturucular, kullanarak bir nesne oluşturduğunuzda çağrılır [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="5f62b-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="5f62b-156">`Console.WriteLine("Hello World!");`_Program. cs \* içindeki çizgiyi aşağıdaki kodla değiştirin ( `<name>` adınızla değiştirin):</span><span class="sxs-lookup"><span data-stu-id="5f62b-156">Replace the line `Console.WriteLine("Hello World!");` in _Program.cs\* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="5f62b-157">Şimdiye kadar derlediğiniz şeyi çalıştıralım.</span><span class="sxs-lookup"><span data-stu-id="5f62b-157">Let's run what you've built so far.</span></span> <span data-ttu-id="5f62b-158">Visual Studio kullanıyorsanız, **Çalıştır** menüsünden **hata ayıklama olmadan Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5f62b-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="5f62b-159">Bir komut satırı kullanıyorsanız, `dotnet run` projenizi oluşturduğunuz dizini yazın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="5f62b-160">Hesap numarasının boş olduğunu fark muydunuz?</span><span class="sxs-lookup"><span data-stu-id="5f62b-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="5f62b-161">Bunun düzeltilmesi zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-161">It's time to fix that.</span></span> <span data-ttu-id="5f62b-162">Nesne oluşturulduğunda hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="5f62b-163">Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="5f62b-164">`BankAccount`Sınıf kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="5f62b-165">Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="5f62b-166">Her yeni hesap oluşturulduğunda bunu artırın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-166">Increment it when each new account is created.</span></span> <span data-ttu-id="5f62b-167">Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="5f62b-168">Sınıfına bir üye bildirimi ekleyin `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="5f62b-169">Sınıfın başındaki açılış ayracından sonra aşağıdaki kod satırını yerleştirin `{` `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="5f62b-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="5f62b-170">Bu bir veri üyesidir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-170">This is a data member.</span></span> <span data-ttu-id="5f62b-171">Bu `private` , yalnızca sınıfın içindeki kodla erişilebilen anlamına gelir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="5f62b-172">Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="5f62b-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="5f62b-173">Ayrıca `static` , tüm nesneler tarafından paylaşıldıkları anlamına gelir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="5f62b-174">Statik olmayan bir değişkenin değeri, nesnenin her bir örneği için benzersizdir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="5f62b-175">Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f62b-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="5f62b-176">Bu satırları şöyle yerleştir `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="5f62b-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="5f62b-177">`dotnet run`Sonuçları görmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="5f62b-178">Mevdular ve çekme işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f62b-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="5f62b-179">Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="5f62b-180">Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim.</span><span class="sxs-lookup"><span data-stu-id="5f62b-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="5f62b-181">Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="5f62b-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="5f62b-182">Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="5f62b-183">Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="5f62b-184">Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="5f62b-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="5f62b-185">Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür.</span><span class="sxs-lookup"><span data-stu-id="5f62b-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="5f62b-186">Birkaç özelliğe ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="5f62b-186">It needs a few properties.</span></span> <span data-ttu-id="5f62b-187">*Transaction.cs*adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f62b-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="5f62b-188">Buna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="5f62b-189">Şimdi sınıfa bir nesne ekleyelim <xref:System.Collections.Generic.List%601> `Transaction` `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="5f62b-190">*BankAccount.cs* dosyanızdaki oluşturucudan sonra aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="5f62b-191"><xref:System.Collections.Generic.List%601>Sınıfı, farklı bir ad alanını içeri aktarmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="5f62b-192">*BankAccount.cs*'nin başlangıcına şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="5f62b-193">Şimdi, öğesini doğru şekilde hesaplaalım `Balance` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-193">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="5f62b-194">Geçerli Bakiye, tüm işlemlerin değerlerini toplayarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-194">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="5f62b-195">Kod şu anda olduğundan, yalnızca hesabın başlangıç bakiyesini alabilir; bu sayede özelliği güncelleştirmeniz gerekir `Balance` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-195">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="5f62b-196">`public decimal Balance { get; }` *BankAccount.cs* içindeki satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-196">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="5f62b-197">Bu örnekte, \***Properties**_ ' in önemli bir yönü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-197">This example shows an important aspect of \***properties**_.</span></span> <span data-ttu-id="5f62b-198">Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="5f62b-198">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="5f62b-199">Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-199">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="5f62b-200">Sonra, `MakeDeposit` ve yöntemlerini uygulayın `MakeWithdrawal` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-200">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="5f62b-201">Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-201">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="5f62b-202">Bu, _\*_özel durum_\*_ kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-202">This introduces the concept of _*_exceptions_*_.</span></span> <span data-ttu-id="5f62b-203">Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-203">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="5f62b-204">Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-204">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="5f62b-205">Burada, `MakeDeposit` depozito miktarı negatifse Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f62b-205">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="5f62b-206">`MakeWithdrawal`Çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f62b-206">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="5f62b-207">Listenin bildiriminden sonra aşağıdaki kodu ekleyin `allTransactions` :</span><span class="sxs-lookup"><span data-stu-id="5f62b-207">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="5f62b-208">[`throw`](../../language-reference/keywords/throw.md)_ İfade \* bir özel durum*oluşturur*.</span><span class="sxs-lookup"><span data-stu-id="5f62b-208">The [`throw`](../../language-reference/keywords/throw.md) statement _*throws*\* an exception.</span></span> <span data-ttu-id="5f62b-209">Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen bloğa yapılan aktarımları denetler `catch` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-209">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="5f62b-210">`catch`Daha sonra bu kodu test etmek için bir blok ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-210">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="5f62b-211">Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-211">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="5f62b-212">Yöntemi zaten yazmış olduğundan `MakeDeposit` , bunu oluşturucudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-212">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="5f62b-213">Tamamlanmış Oluşturucu şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="5f62b-213">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="5f62b-214"><xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli tarih ve saati döndüren bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="5f62b-214"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="5f62b-215">Bu `Main` , yeni bir oluşturan kodun ardından, yönteyinizdeki birkaç mevdug ve çekme bilgilerini ekleyerek test edin `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="5f62b-215">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="5f62b-216">Daha sonra, negatif bakiyeyle bir hesap oluşturmayı deneyerek hata koşullarını yakalamak için test edin.</span><span class="sxs-lookup"><span data-stu-id="5f62b-216">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="5f62b-217">Yeni eklediğiniz kodun ardından aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-217">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="5f62b-218">[ `try` Ve `catch` deyimlerini](../../language-reference/keywords/try-catch.md) , özel durum oluşturabilecek bir kod bloğunu işaretlemek ve beklediğinizi bu hataları yakalamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5f62b-218">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="5f62b-219">Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-219">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="5f62b-220">Yönteminizin sonuna aşağıdaki kodu ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="5f62b-220">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="5f62b-221">Dosyayı kaydedin ve `dotnet run` denemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-221">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="5f62b-222">Sınama-tüm işlemleri günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="5f62b-222">Challenge - log all transactions</span></span>

<span data-ttu-id="5f62b-223">Bu öğreticiyi bitirebilmeniz için, `GetAccountHistory` işlem geçmişi için oluşturan yöntemini yazabilirsiniz `string` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-223">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="5f62b-224">Bu yöntemi `BankAccount` türe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-224">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="5f62b-225">Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f62b-225">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="5f62b-226">Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-226">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="5f62b-227">Yeni bir karakter `\t` .</span><span class="sxs-lookup"><span data-stu-id="5f62b-227">One new character is `\t`.</span></span> <span data-ttu-id="5f62b-228">Bu, çıktıyı biçimlendirmek için bir sekme ekler.</span><span class="sxs-lookup"><span data-stu-id="5f62b-228">That inserts a tab to format the output.</span></span>

<span data-ttu-id="5f62b-229">*Program.cs*içinde test etmek için bu satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5f62b-229">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="5f62b-230">Sonuçları görmek için programınızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5f62b-230">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5f62b-231">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5f62b-231">Next steps</span></span>

<span data-ttu-id="5f62b-232">Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)deponuzda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-232">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="5f62b-233">[Nesne yönelimli programlama](object-oriented-programming.md) öğreticisiyle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f62b-233">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="5f62b-234">Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5f62b-234">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="5f62b-235">If ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="5f62b-235">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="5f62b-236">While ekstresi</span><span class="sxs-lookup"><span data-stu-id="5f62b-236">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="5f62b-237">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="5f62b-237">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="5f62b-238">For deyimleri</span><span class="sxs-lookup"><span data-stu-id="5f62b-238">For statement</span></span>](../../language-reference/keywords/for.md)
