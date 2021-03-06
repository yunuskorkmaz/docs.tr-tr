---
title: Sınıflar ve nesneler-C# öğreticisine giriş
description: İlk C# programınızı oluşturun ve nesne yönelimli kavramları keşfedebilirsiniz
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 3da445e6c656628fffdb9ef9384fb1a1c556a2cd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255424"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="0b402-103">Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet</span><span class="sxs-lookup"><span data-stu-id="0b402-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="0b402-104">Bu öğreticide, bir konsol uygulaması oluşturacaksınız ve C# dilinin bir parçası olan temel nesne yönelimli özellikleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0b402-104">In this tutorial, you'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b402-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0b402-105">Prerequisites</span></span>

<span data-ttu-id="0b402-106">Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="0b402-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="0b402-107">Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="0b402-108">Windows 'ta, Visual Studio 2019 ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-108">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="0b402-109">Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](../../tour-of-csharp/tutorials/local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0b402-109">For setup instructions, see [Set up your local environment](../../tour-of-csharp/tutorials/local-environment.md).</span></span>

## <a name="create-your-application"></a><span data-ttu-id="0b402-110">Uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b402-110">Create your application</span></span>

<span data-ttu-id="0b402-111">Bir Terminal penceresi kullanarak, *sınıflar* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b402-111">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="0b402-112">Uygulamanızı burada oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0b402-112">You'll build your application there.</span></span> <span data-ttu-id="0b402-113">Bu dizine geçin ve `dotnet new console` konsol penceresinde yazın.</span><span class="sxs-lookup"><span data-stu-id="0b402-113">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="0b402-114">Bu komut uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b402-114">This command creates your application.</span></span> <span data-ttu-id="0b402-115">*Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0b402-115">Open *Program.cs*.</span></span> <span data-ttu-id="0b402-116">Şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="0b402-116">It should look like this:</span></span>

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

<span data-ttu-id="0b402-117">Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0b402-117">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="0b402-118">Genellikle geliştiriciler her bir sınıfı farklı bir metin dosyasında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b402-118">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="0b402-119">Bu, bir program boyutunun büyüdükçe daha kolay yönetilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b402-119">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="0b402-120">*Classes* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b402-120">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="0b402-121">Bu dosya, \***Banka hesabı** _ tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="0b402-121">This file will contain the definition of a \***bank account** _.</span></span> <span data-ttu-id="0b402-122">Nesne odaklı programlama, _ *_sınıfları_* \* biçiminde türler oluşturarak kodu düzenler.</span><span class="sxs-lookup"><span data-stu-id="0b402-122">Object Oriented programming organizes code by creating types in the form of _\*_classes_\*\*.</span></span> <span data-ttu-id="0b402-123">Bu sınıflar, belirli bir varlığı temsil eden kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="0b402-123">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="0b402-124">`BankAccount`Sınıfı bir banka hesabını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b402-124">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="0b402-125">Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="0b402-125">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="0b402-126">Bu öğreticide, banka hesabı bu davranışı destekler:</span><span class="sxs-lookup"><span data-stu-id="0b402-126">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="0b402-127">Bu, banka hesabını benzersiz bir şekilde tanımlayan 10 basamaklı bir sayı içerir.</span><span class="sxs-lookup"><span data-stu-id="0b402-127">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="0b402-128">Sahiplerinin adını veya adlarını depolayan bir dizesi vardır.</span><span class="sxs-lookup"><span data-stu-id="0b402-128">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="0b402-129">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="0b402-129">The balance can be retrieved.</span></span>
1. <span data-ttu-id="0b402-130">Mevduat kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0b402-130">It accepts deposits.</span></span>
1. <span data-ttu-id="0b402-131">Çekme kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0b402-131">It accepts withdrawals.</span></span>
1. <span data-ttu-id="0b402-132">İlk bakiye pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b402-132">The initial balance must be positive.</span></span>
1. <span data-ttu-id="0b402-133">Çekme işlemleri negatif bir bakiyeye neden olamaz.</span><span class="sxs-lookup"><span data-stu-id="0b402-133">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="0b402-134">Banka hesap türünü tanımlayın</span><span class="sxs-lookup"><span data-stu-id="0b402-134">Define the bank account type</span></span>

<span data-ttu-id="0b402-135">Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-135">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="0b402-136">**Dosya: New** komutunu kullanarak yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b402-136">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="0b402-137">*BankAccount.cs* olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0b402-137">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="0b402-138">Aşağıdaki kodu *BankAccount.cs* dosyanıza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-138">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="0b402-139">Başlamadan önce, derleydiklerinize göz atalım.</span><span class="sxs-lookup"><span data-stu-id="0b402-139">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="0b402-140">`namespace`Bildirimi, kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b402-140">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="0b402-141">Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-141">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="0b402-142">`public class BankAccount` oluşturmakta olduğunuz sınıfı veya türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b402-142">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="0b402-143">`{`Sınıf bildirimini izleyen ve içindeki her şey, `}` sınıfının durumunu ve davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b402-143">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="0b402-144">Sınıfın beş \***üyesi** _ `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-144">There are five \***members** _ of the `BankAccount` class.</span></span> <span data-ttu-id="0b402-145">İlk üçü _\*_özelliklerdir_\*_.</span><span class="sxs-lookup"><span data-stu-id="0b402-145">The first three are _*_properties_*_.</span></span> <span data-ttu-id="0b402-146">Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b402-146">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="0b402-147">Son ikisi _ *_Yöntemler_* \* ' dir.</span><span class="sxs-lookup"><span data-stu-id="0b402-147">The last two are _\*_methods_\*\*.</span></span> <span data-ttu-id="0b402-148">Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="0b402-148">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="0b402-149">Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b402-149">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="0b402-150">Yeni bir hesap açın</span><span class="sxs-lookup"><span data-stu-id="0b402-150">Open a new account</span></span>

<span data-ttu-id="0b402-151">Uygulanacak ilk özellik bir banka hesabı açmak.</span><span class="sxs-lookup"><span data-stu-id="0b402-151">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="0b402-152">Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b402-152">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="0b402-153">Türünde yeni bir nesne oluşturmak, `BankAccount` Bu değerleri atayan bir \***Oluşturucu** _ tanımlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b402-153">Creating a new object of the `BankAccount` type means defining a \***constructor** _ that assigns those values.</span></span> <span data-ttu-id="0b402-154">_ \*_Oluşturucusu_\*\*, sınıfıyla aynı ada sahip olan bir üyedir.</span><span class="sxs-lookup"><span data-stu-id="0b402-154">A _ *_constructor_*\* is a member that has the same name as the class.</span></span> <span data-ttu-id="0b402-155">Bu sınıf türündeki nesneleri başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b402-155">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="0b402-156">Türe aşağıdaki oluşturucuyu ekleyin `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-156">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="0b402-157">Aşağıdaki kodu bildiriminin üzerine yerleştirin `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="0b402-157">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="0b402-158">Oluşturucular, kullanarak bir nesne oluşturduğunuzda çağrılır [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="0b402-158">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="0b402-159">`Console.WriteLine("Hello World!");` *Program.cs* içindeki satırı aşağıdaki kodla değiştirin ( `<name>` adınızla değiştirin):</span><span class="sxs-lookup"><span data-stu-id="0b402-159">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="0b402-160">Şimdiye kadar derlediğiniz şeyi çalıştıralım.</span><span class="sxs-lookup"><span data-stu-id="0b402-160">Let's run what you've built so far.</span></span> <span data-ttu-id="0b402-161">Visual Studio kullanıyorsanız, **Çalıştır** menüsünden **hata ayıklama olmadan Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="0b402-161">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="0b402-162">Bir komut satırı kullanıyorsanız, `dotnet run` projenizi oluşturduğunuz dizini yazın.</span><span class="sxs-lookup"><span data-stu-id="0b402-162">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="0b402-163">Hesap numarasının boş olduğunu fark muydunuz?</span><span class="sxs-lookup"><span data-stu-id="0b402-163">Did you notice that the account number is blank?</span></span> <span data-ttu-id="0b402-164">Bunun düzeltilmesi zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="0b402-164">It's time to fix that.</span></span> <span data-ttu-id="0b402-165">Nesne oluşturulduğunda hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b402-165">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="0b402-166">Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b402-166">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="0b402-167">`BankAccount`Sınıf kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b402-167">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="0b402-168">Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır.</span><span class="sxs-lookup"><span data-stu-id="0b402-168">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="0b402-169">Her yeni hesap oluşturulduğunda bunu artırın.</span><span class="sxs-lookup"><span data-stu-id="0b402-169">Increment it when each new account is created.</span></span> <span data-ttu-id="0b402-170">Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.</span><span class="sxs-lookup"><span data-stu-id="0b402-170">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="0b402-171">Sınıfına bir üye bildirimi ekleyin `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-171">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="0b402-172">Sınıfın başındaki açılış ayracından sonra aşağıdaki kod satırını yerleştirin `{` `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="0b402-172">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="0b402-173">Bu bir veri üyesidir.</span><span class="sxs-lookup"><span data-stu-id="0b402-173">This is a data member.</span></span> <span data-ttu-id="0b402-174">Bu `private` , yalnızca sınıfın içindeki kodla erişilebilen anlamına gelir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-174">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="0b402-175">Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="0b402-175">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="0b402-176">Ayrıca `static` , tüm nesneler tarafından paylaşıldıkları anlamına gelir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-176">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="0b402-177">Statik olmayan bir değişkenin değeri, nesnenin her bir örneği için benzersizdir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-177">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="0b402-178">Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0b402-178">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="0b402-179">Bu satırları şöyle yerleştir `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="0b402-179">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="0b402-180">`dotnet run`Sonuçları görmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="0b402-180">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="0b402-181">Mevdular ve çekme işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b402-181">Create deposits and withdrawals</span></span>

<span data-ttu-id="0b402-182">Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b402-182">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="0b402-183">Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim.</span><span class="sxs-lookup"><span data-stu-id="0b402-183">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="0b402-184">Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="0b402-184">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="0b402-185">Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b402-185">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="0b402-186">Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="0b402-186">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="0b402-187">Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="0b402-187">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="0b402-188">Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0b402-188">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="0b402-189">Birkaç özelliğe ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="0b402-189">It needs a few properties.</span></span> <span data-ttu-id="0b402-190">*Transaction.cs* adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b402-190">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="0b402-191">Buna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-191">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="0b402-192">Şimdi sınıfa bir nesne ekleyelim <xref:System.Collections.Generic.List%601> `Transaction` `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="0b402-192">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="0b402-193">*BankAccount.cs* dosyanızdaki oluşturucudan sonra aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-193">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="0b402-194"><xref:System.Collections.Generic.List%601>Sınıfı, farklı bir ad alanını içeri aktarmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0b402-194">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="0b402-195">*BankAccount.cs*'nin başlangıcına şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-195">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="0b402-196">Şimdi, öğesini doğru şekilde hesaplaalım `Balance` .</span><span class="sxs-lookup"><span data-stu-id="0b402-196">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="0b402-197">Geçerli Bakiye, tüm işlemlerin değerlerini toplayarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0b402-197">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="0b402-198">Kod şu anda olduğundan, yalnızca hesabın başlangıç bakiyesini alabilir; bu sayede özelliği güncelleştirmeniz gerekir `Balance` .</span><span class="sxs-lookup"><span data-stu-id="0b402-198">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="0b402-199">`public decimal Balance { get; }` *BankAccount.cs* içindeki satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0b402-199">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="0b402-200">Bu örnekte, ***özelliklerin*** önemli bir yönü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b402-200">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="0b402-201">Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="0b402-201">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="0b402-202">Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.</span><span class="sxs-lookup"><span data-stu-id="0b402-202">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="0b402-203">Sonra, `MakeDeposit` ve yöntemlerini uygulayın `MakeWithdrawal` .</span><span class="sxs-lookup"><span data-stu-id="0b402-203">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="0b402-204">Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b402-204">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="0b402-205">Bu, ***özel durum*** kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="0b402-205">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="0b402-206">Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0b402-206">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="0b402-207">Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b402-207">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="0b402-208">Burada, `MakeDeposit` depozito miktarı negatifse Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b402-208">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="0b402-209">`MakeWithdrawal`Çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b402-209">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="0b402-210">Listenin bildiriminden sonra aşağıdaki kodu ekleyin `allTransactions` :</span><span class="sxs-lookup"><span data-stu-id="0b402-210">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="0b402-211">[`throw`](../../language-reference/keywords/throw.md)İfade bir özel durum **oluşturur** .</span><span class="sxs-lookup"><span data-stu-id="0b402-211">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="0b402-212">Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen bloğa yapılan aktarımları denetler `catch` .</span><span class="sxs-lookup"><span data-stu-id="0b402-212">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="0b402-213">`catch`Daha sonra bu kodu test etmek için bir blok ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-213">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="0b402-214">Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b402-214">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="0b402-215">Yöntemi zaten yazmış olduğundan `MakeDeposit` , bunu oluşturucudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="0b402-215">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="0b402-216">Tamamlanmış Oluşturucu şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="0b402-216">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="0b402-217"><xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli tarih ve saati döndüren bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="0b402-217"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="0b402-218">Bu `Main` , yeni bir oluşturan kodun ardından, yönteyinizdeki birkaç mevdug ve çekme bilgilerini ekleyerek test edin `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="0b402-218">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="0b402-219">Daha sonra, negatif bakiyeyle bir hesap oluşturmayı deneyerek hata koşullarını yakalamak için test edin.</span><span class="sxs-lookup"><span data-stu-id="0b402-219">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="0b402-220">Yeni eklediğiniz kodun ardından aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-220">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="0b402-221">[ `try` Ve `catch` deyimlerini](../../language-reference/keywords/try-catch.md) , özel durum oluşturabilecek bir kod bloğunu işaretlemek ve beklediğinizi bu hataları yakalamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0b402-221">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="0b402-222">Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-222">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="0b402-223">Yönteminizin sonuna aşağıdaki kodu ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="0b402-223">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="0b402-224">Dosyayı kaydedin ve `dotnet run` denemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="0b402-224">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="0b402-225">Sınama-tüm işlemleri günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="0b402-225">Challenge - log all transactions</span></span>

<span data-ttu-id="0b402-226">Bu öğreticiyi bitirebilmeniz için, `GetAccountHistory` işlem geçmişi için oluşturan yöntemini yazabilirsiniz `string` .</span><span class="sxs-lookup"><span data-stu-id="0b402-226">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="0b402-227">Bu yöntemi `BankAccount` türe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-227">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="0b402-228">Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b402-228">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="0b402-229">Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz.</span><span class="sxs-lookup"><span data-stu-id="0b402-229">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="0b402-230">Yeni bir karakter `\t` .</span><span class="sxs-lookup"><span data-stu-id="0b402-230">One new character is `\t`.</span></span> <span data-ttu-id="0b402-231">Bu, çıktıyı biçimlendirmek için bir sekme ekler.</span><span class="sxs-lookup"><span data-stu-id="0b402-231">That inserts a tab to format the output.</span></span>

<span data-ttu-id="0b402-232">*Program.cs* içinde test etmek için bu satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b402-232">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="0b402-233">Sonuçları görmek için programınızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b402-233">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0b402-234">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0b402-234">Next steps</span></span>

<span data-ttu-id="0b402-235">Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)deponuzda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-235">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="0b402-236">[Nesne yönelimli programlama](object-oriented-programming.md) öğreticisiyle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b402-236">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="0b402-237">Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b402-237">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="0b402-238">If ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="0b402-238">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="0b402-239">While ekstresi</span><span class="sxs-lookup"><span data-stu-id="0b402-239">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="0b402-240">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="0b402-240">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="0b402-241">For deyimleri</span><span class="sxs-lookup"><span data-stu-id="0b402-241">For statement</span></span>](../../language-reference/keywords/for.md)
