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
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="ac3b0-103">Sınıflar ve nesneler ile nesne odaklı programlamayı keşfet</span><span class="sxs-lookup"><span data-stu-id="ac3b0-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="ac3b0-104">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="ac3b0-105">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ac3b0-106">Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="ac3b0-107">Uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac3b0-107">Create your application</span></span>

<span data-ttu-id="ac3b0-108">Bir Terminal penceresi kullanarak, *sınıflar*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="ac3b0-109">Uygulamanızı burada oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-109">You'll build your application there.</span></span> <span data-ttu-id="ac3b0-110">Bu dizine geçin ve `dotnet new console` konsol penceresinde yazın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="ac3b0-111">Bu komut uygulamanızı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-111">This command creates your application.</span></span> <span data-ttu-id="ac3b0-112">*Program.cs*'i açın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-112">Open *Program.cs*.</span></span> <span data-ttu-id="ac3b0-113">Şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-113">It should look like this:</span></span>

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

<span data-ttu-id="ac3b0-114">Bu öğreticide, bir banka hesabını temsil eden yeni türler oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="ac3b0-115">Genellikle geliştiriciler her bir sınıfı farklı bir metin dosyasında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="ac3b0-116">Bu, bir program boyutunun büyüdükçe daha kolay yönetilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="ac3b0-117">*Classes* dizininde *BankAccount.cs* adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="ac3b0-118">Bu dosya, bir ***Banka hesabının***tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="ac3b0-119">Nesne odaklı programlama, ***sınıf***biçiminde türler oluşturarak kodu düzenler.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="ac3b0-120">Bu sınıflar, belirli bir varlığı temsil eden kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="ac3b0-121">`BankAccount`Sınıfı bir banka hesabını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="ac3b0-122">Kod, Yöntemler ve özellikler aracılığıyla belirli işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="ac3b0-123">Bu öğreticide, banka hesabı bu davranışı destekler:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="ac3b0-124">Bu, banka hesabını benzersiz bir şekilde tanımlayan 10 basamaklı bir sayı içerir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="ac3b0-125">Sahiplerinin adını veya adlarını depolayan bir dizesi vardır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="ac3b0-126">Bakiye alınabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="ac3b0-127">Mevduat kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-127">It accepts deposits.</span></span>
1. <span data-ttu-id="ac3b0-128">Çekme kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="ac3b0-129">İlk bakiye pozitif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="ac3b0-130">Çekme işlemleri negatif bir bakiyeye neden olamaz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="ac3b0-131">Banka hesap türünü tanımlayın</span><span class="sxs-lookup"><span data-stu-id="ac3b0-131">Define the bank account type</span></span>

<span data-ttu-id="ac3b0-132">Bu davranışı tanımlayan bir sınıfın temellerini oluşturarak başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="ac3b0-133">**Dosya: New** komutunu kullanarak yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-133">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="ac3b0-134">*BankAccount.cs*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="ac3b0-135">Aşağıdaki kodu *BankAccount.cs* dosyanıza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="ac3b0-136">Başlamadan önce, derleydiklerinize göz atalım.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="ac3b0-137">`namespace`Bildirimi, kodunuzu mantıksal olarak düzenlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="ac3b0-138">Bu öğretici nispeten küçüktür, bu nedenle tüm kodu bir ad alanına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="ac3b0-139">`public class BankAccount` oluşturmakta olduğunuz sınıfı veya türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="ac3b0-140">`{`Sınıf bildirimini izleyen ve içindeki her şey, `}` sınıfının durumunu ve davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="ac3b0-141">Sınıfının beş ***üyesi*** vardır `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-141">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="ac3b0-142">İlk üçü ***özelliklerdir***.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-142">The first three are ***properties***.</span></span> <span data-ttu-id="ac3b0-143">Özellikler veri öğeleridir ve doğrulamayı veya diğer kuralları zorlayan koda sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="ac3b0-144">Son ikisi ***metodlardır***.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-144">The last two are ***methods***.</span></span> <span data-ttu-id="ac3b0-145">Yöntemler, tek bir işlevi gerçekleştiren kod bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="ac3b0-146">Her üyenin adını okumak, siz veya başka bir geliştirici tarafından sınıfın ne yaptığını anlamak için yeterli bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="ac3b0-147">Yeni bir hesap açın</span><span class="sxs-lookup"><span data-stu-id="ac3b0-147">Open a new account</span></span>

<span data-ttu-id="ac3b0-148">Uygulanacak ilk özellik bir banka hesabı açmak.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="ac3b0-149">Bir müşteri bir hesabı açtığında, bir başlangıç bakiyesi ve bu hesabın sahibi veya sahipleri hakkında bilgi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="ac3b0-150">Türünde yeni bir nesne oluşturmak, `BankAccount` Bu değerleri atayan bir ***Oluşturucu*** tanımlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-150">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="ac3b0-151">***Oluşturucu*** , sınıfıyla aynı ada sahip olan bir üyedir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-151">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="ac3b0-152">Bu sınıf türündeki nesneleri başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="ac3b0-153">Türe aşağıdaki oluşturucuyu ekleyin `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="ac3b0-154">Aşağıdaki kodu bildiriminin üzerine yerleştirin `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="ac3b0-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="ac3b0-155">Oluşturucular, kullanarak bir nesne oluşturduğunuzda çağrılır [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="ac3b0-156">`Console.WriteLine("Hello World!");` *Program.cs* içindeki satırı aşağıdaki kodla değiştirin ( `<name>` adınızla değiştirin):</span><span class="sxs-lookup"><span data-stu-id="ac3b0-156">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="ac3b0-157">Şimdiye kadar derlediğiniz şeyi çalıştıralım.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-157">Let's run what you've built so far.</span></span> <span data-ttu-id="ac3b0-158">Visual Studio kullanıyorsanız, **Çalıştır** menüsünden **hata ayıklama olmadan Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="ac3b0-159">Bir komut satırı kullanıyorsanız, `dotnet run` projenizi oluşturduğunuz dizini yazın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="ac3b0-160">Hesap numarasının boş olduğunu fark muydunuz?</span><span class="sxs-lookup"><span data-stu-id="ac3b0-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="ac3b0-161">Bunun düzeltilmesi zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-161">It's time to fix that.</span></span> <span data-ttu-id="ac3b0-162">Nesne oluşturulduğunda hesap numarası atanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="ac3b0-163">Ancak bunu oluşturmak için çağıranın sorumluluğunda olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="ac3b0-164">`BankAccount`Sınıf kodu, yeni hesap numaralarının nasıl atanacağını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="ac3b0-165">Bunu yapmanın basit bir yolu, 10 basamaklı bir sayıyla başlamamaktır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="ac3b0-166">Her yeni hesap oluşturulduğunda bunu artırın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-166">Increment it when each new account is created.</span></span> <span data-ttu-id="ac3b0-167">Son olarak, bir nesne oluşturulduğunda geçerli hesap numarasını saklayın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="ac3b0-168">Sınıfına bir üye bildirimi ekleyin `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="ac3b0-169">Sınıfın başındaki açılış ayracından sonra aşağıdaki kod satırını yerleştirin `{` `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="ac3b0-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="ac3b0-170">Bu bir veri üyesidir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-170">This is a data member.</span></span> <span data-ttu-id="ac3b0-171">Bu `private` , yalnızca sınıfın içindeki kodla erişilebilen anlamına gelir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="ac3b0-172">Bu, genel sorumlulukları (hesap numarası gibi) özel uygulamadan (hesap numaraları nasıl oluşturulur) ayırmaktan bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="ac3b0-173">Ayrıca `static` , tüm nesneler tarafından paylaşıldıkları anlamına gelir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="ac3b0-174">Statik olmayan bir değişkenin değeri, nesnenin her bir örneği için benzersizdir `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="ac3b0-175">Hesap numarasını atamak için oluşturucuya aşağıdaki iki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="ac3b0-176">Bu satırları şöyle yerleştir `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="ac3b0-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="ac3b0-177">`dotnet run`Sonuçları görmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="ac3b0-178">Mevdular ve çekme işlemleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac3b0-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="ac3b0-179">Banka hesabı sınıfınızın, doğru şekilde çalışması için mevdular ve çekme alları kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="ac3b0-180">Hesap için her bir işlemin günlüğünü oluşturarak mevduları ve çekme bilgilerini uygulayalim.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="ac3b0-181">Bu, her bir işlemin bakiyesini güncelleştirmek için birkaç avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="ac3b0-182">Geçmiş, tüm işlemleri denetlemek ve günlük bakiyeleri yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="ac3b0-183">Gerektiğinde, tüm işlemlerin geçmişinden gelen dengeyi hesaplarken, düzeltilen tek bir işlemdeki tüm hatalar, sonraki hesaplamanın bakiyesine doğru şekilde yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="ac3b0-184">Bir işlemi temsil etmek için yeni bir tür oluşturarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="ac3b0-185">Bu, herhangi bir sorumluluğu bulunmayan basit bir türdür.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="ac3b0-186">Birkaç özelliğe ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-186">It needs a few properties.</span></span> <span data-ttu-id="ac3b0-187">*Transaction.cs*adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="ac3b0-188">Buna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="ac3b0-189">Şimdi sınıfa bir nesne ekleyelim <xref:System.Collections.Generic.List%601> `Transaction` `BankAccount` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="ac3b0-190">*BankAccount.cs* dosyanızdaki oluşturucudan sonra aşağıdaki bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="ac3b0-191"><xref:System.Collections.Generic.List%601>Sınıfı, farklı bir ad alanını içeri aktarmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="ac3b0-192">*BankAccount.cs*'nin başlangıcına şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="ac3b0-193">Şimdi, raporun nasıl bildirileceğini değiştirelim `Balance` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-193">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="ac3b0-194">Bu, tüm işlemlerin değerlerini toplayarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-194">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="ac3b0-195">`Balance` `BankAccount` Sınıfında bildirimini aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-195">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="ac3b0-196">Bu örnekte, ***özelliklerin***önemli bir yönü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-196">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="ac3b0-197">Artık, başka bir programcı değer istediğinde bakiyeyi hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-197">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="ac3b0-198">Hesaplama tüm işlemleri numaralandırır ve toplamı geçerli Bakiye olarak verir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-198">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="ac3b0-199">Sonra, `MakeDeposit` ve yöntemlerini uygulayın `MakeWithdrawal` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-199">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="ac3b0-200">Bu yöntemler, son iki kuralı zorunlu tutar: ilk Bakiyenin pozitif olması ve tüm çekme allarının negatif bir bakiye oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-200">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="ac3b0-201">Bu, ***özel durum***kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-201">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="ac3b0-202">Bir yöntemin işini başarıyla tamamlayamadığını belirten standart yol, bir özel durum oluşturmak şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-202">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="ac3b0-203">Özel durum türü ve onunla ilişkili ileti hatayı anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-203">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="ac3b0-204">Burada, `MakeDeposit` depozito miktarı negatifse Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-204">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="ac3b0-205">`MakeWithdrawal`Çekme miktarı negatifse veya çekme sonuçları negatif bir bakiyeye uygulanırsa Yöntem bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-205">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="ac3b0-206">Listenin bildiriminden sonra aşağıdaki kodu ekleyin `allTransactions` :</span><span class="sxs-lookup"><span data-stu-id="ac3b0-206">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="ac3b0-207">[`throw`](../../language-reference/keywords/throw.md)İfade bir özel durum **oluşturur** .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-207">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="ac3b0-208">Geçerli bloğun yürütülmesi sonlanır ve çağrı yığınında bulunan ilk eşleşen bloğa yapılan aktarımları denetler `catch` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-208">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="ac3b0-209">`catch`Daha sonra bu kodu test etmek için bir blok ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-209">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="ac3b0-210">Oluşturucunun, bakiyeyi doğrudan güncelleştirmek yerine bir ilk işlem eklemesi için bir değişiklik alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-210">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="ac3b0-211">Yöntemi zaten yazmış olduğundan `MakeDeposit` , bunu oluşturucudan çağırın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-211">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="ac3b0-212">Tamamlanmış Oluşturucu şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-212">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="ac3b0-213"><xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli tarih ve saati döndüren bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-213"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="ac3b0-214">Bu `Main` , yeni bir oluşturan kodun ardından, yönteyinizdeki birkaç mevdug ve çekme bilgilerini ekleyerek test edin `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="ac3b0-214">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="ac3b0-215">Daha sonra, negatif bakiyeyle bir hesap oluşturmayı deneyerek hata koşullarını yakalamak için test edin.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-215">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="ac3b0-216">Yeni eklediğiniz kodun ardından aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-216">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="ac3b0-217">[ `try` Ve `catch` deyimlerini](../../language-reference/keywords/try-catch.md) , özel durum oluşturabilecek bir kod bloğunu işaretlemek ve beklediğinizi bu hataları yakalamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-217">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="ac3b0-218">Negatif bir bakiye için özel durum oluşturan kodu test etmek için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-218">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="ac3b0-219">Yönteminizin sonuna aşağıdaki kodu ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="ac3b0-219">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="ac3b0-220">Dosyayı kaydedin ve `dotnet run` denemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-220">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="ac3b0-221">Sınama-tüm işlemleri günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="ac3b0-221">Challenge - log all transactions</span></span>

<span data-ttu-id="ac3b0-222">Bu öğreticiyi bitirebilmeniz için, `GetAccountHistory` işlem geçmişi için oluşturan yöntemini yazabilirsiniz `string` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-222">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="ac3b0-223">Bu yöntemi `BankAccount` türe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-223">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="ac3b0-224">Bu, <xref:System.Text.StringBuilder> her işlem için bir satır içeren bir dizeyi biçimlendirmek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-224">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="ac3b0-225">Bu öğreticilerde daha önce dize biçimlendirme kodunu gördünüz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-225">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="ac3b0-226">Yeni bir karakter `\t` .</span><span class="sxs-lookup"><span data-stu-id="ac3b0-226">One new character is `\t`.</span></span> <span data-ttu-id="ac3b0-227">Bu, çıktıyı biçimlendirmek için bir sekme ekler.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-227">That inserts a tab to format the output.</span></span>

<span data-ttu-id="ac3b0-228">*Program.cs*içinde test etmek için bu satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-228">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="ac3b0-229">Sonuçları görmek için programınızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-229">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ac3b0-230">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ac3b0-230">Next steps</span></span>

<span data-ttu-id="ac3b0-231">Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/)deponuzda görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-231">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="ac3b0-232">[Nesne yönelimli programlama](object-oriented-programming.md) öğreticisiyle devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac3b0-232">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="ac3b0-233">Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac3b0-233">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="ac3b0-234">If ve else deyimi</span><span class="sxs-lookup"><span data-stu-id="ac3b0-234">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="ac3b0-235">While ekstresi</span><span class="sxs-lookup"><span data-stu-id="ac3b0-235">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="ac3b0-236">Do deyimi</span><span class="sxs-lookup"><span data-stu-id="ac3b0-236">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="ac3b0-237">For deyimleri</span><span class="sxs-lookup"><span data-stu-id="ac3b0-237">For statement</span></span>](../../language-reference/keywords/for.md)
