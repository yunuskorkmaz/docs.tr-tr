---
title: 'İzlenecek yol: C kullanarak bir nesneyi kalıcı hale getirme #'
ms.date: 04/26/2018
ms.openlocfilehash: bbe239008629d687084af7e28a75fa68560ca0ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796073"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="d5cb8-102">İzlenecek yol: C kullanarak bir nesneyi kalıcı hale getirme\#</span><span class="sxs-lookup"><span data-stu-id="d5cb8-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="d5cb8-103">Nesneleri, değerleri depolamanızı ve nesnenin bir sonraki açılışında bunları almanızı sağlayan örnekler arasında bir nesnenin verilerini kalıcı hale getirmek için serileştirme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="d5cb8-104">Bu kılavuzda, temel `Loan` bir nesne oluşturacak ve verilerini bir dosyaya kalıcı hale getirilecektir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="d5cb8-105">Daha sonra nesneyi yeniden oluşturduğunuzda dosyadaki verileri buradan alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5cb8-106">Bu örnek, dosya henüz yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="d5cb8-107">Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için izni `Create` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="d5cb8-108">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="d5cb8-109">Dosya zaten varsa, uygulamanın daha az izne sahip yalnızca `Write` izne ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="d5cb8-110">Mümkün olduğunda, dağıtım sırasında dosyayı oluşturmak ve yalnızca tek bir dosyaya (bir klasör için `Read` izinler oluşturmak yerine) izin vermek daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="d5cb8-111">Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5cb8-112">Bu örnek, verileri bir ikili biçim dosyasında depolar.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="d5cb8-113">Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d5cb8-114">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="d5cb8-114">Prerequisites</span></span>

- <span data-ttu-id="d5cb8-115">Derlemek ve çalıştırmak için [.NET Core SDK](https://dotnet.microsoft.com/download)' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="d5cb8-116">Henüz yapmadıysanız, en sevdiğiniz kod düzenleyicinizi yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="d5cb8-117">Bir kod Düzenleyicisi yüklemeniz mı gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="d5cb8-117">Need to install a code editor?</span></span> <span data-ttu-id="d5cb8-118">[Visual Studio 'yu](https://visualstudio.com/downloads)deneyin!</span><span class="sxs-lookup"><span data-stu-id="d5cb8-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="d5cb8-119">Örnek, C# 7,3 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-119">The example requires C# 7.3.</span></span> <span data-ttu-id="d5cb8-120">Bkz [. C# dil sürümünü seçme](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="d5cb8-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="d5cb8-121">Örnek kodu, [.NET örnekleri GitHub deposunda](https://github.com/dotnet/samples/tree/master/csharp/serialization)çevrimiçi olarak inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="d5cb8-122">Kredi nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5cb8-122">Creating the loan object</span></span>

<span data-ttu-id="d5cb8-123">İlk adım, sınıfını kullanan bir `Loan` sınıf ve konsol uygulaması oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="d5cb8-124">Yeni bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-124">Create a new application.</span></span> <span data-ttu-id="d5cb8-125">Adlı `dotnet new console -o serialization` `serialization`bir alt dizinde yeni bir konsol uygulaması oluşturmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="d5cb8-126">Düzenleyicinizde uygulamayı açın ve adlı `Loan.cs`yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="d5cb8-127">Sınıfınıza `Loan` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="d5cb8-128">Ayrıca, `Loan` sınıfını kullanan bir uygulama da oluşturmanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="d5cb8-129">Kredi nesnesini seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="d5cb8-129">Serialize the loan object</span></span>

1. <span data-ttu-id="d5cb8-130">`Program.cs` dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-130">Open `Program.cs`.</span></span> <span data-ttu-id="d5cb8-131">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="d5cb8-132">`PropertyChanged` Olay için bir olay işleyicisi ve `Loan` nesneyi değiştirmek ve değişiklikleri göstermek için birkaç satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="d5cb8-133">Eklemeleri aşağıdaki kodda görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="d5cb8-134">Bu noktada, kodu çalıştırabilir ve geçerli çıktıyı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="d5cb8-135">Bu uygulamayı sürekli olarak çalıştırmak her zaman aynı değerleri yazar.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="d5cb8-136">Programı her çalıştırdığınızda yeni bir kredi nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="d5cb8-137">Gerçek dünyada, faiz oranları düzenli aralıklarla değişir, ancak uygulama her çalıştırıldığında her zaman gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="d5cb8-138">Serileştirme kodu, uygulamanın örnekleri arasındaki en son faiz oranını koruduğunuzdan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="d5cb8-139">Bir sonraki adımda, yalnızca kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="d5cb8-140">Nesneyi kalıcı hale getirmek için serileştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="d5cb8-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="d5cb8-141">Kredi sınıfının değerlerini kalıcı hale getirmek için, önce sınıfı `Serializable` özniteliğiyle işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="d5cb8-142">Aşağıdaki kodu ödünç verme sınıfı tanımının üzerine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="d5cb8-143">, <xref:System.SerializableAttribute> Derleyiciye sınıftaki her şeyin bir dosyaya kalıcı olarak devam edebilir olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="d5cb8-144">`PropertyChanged` Olay, nesne grafiğinin depolanması gereken parçasını temsil etmediğinden, serileştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="d5cb8-145">Bunun yapılması, bu olaya eklenmiş tüm nesneleri serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="d5cb8-146">Olay işleyicisi için alan bildirimine ekleyebilirsiniz <xref:System.NonSerializedAttribute> `PropertyChanged`</span><span class="sxs-lookup"><span data-stu-id="d5cb8-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="d5cb8-147">C# 7,3 ' den başlayarak, `field` hedef değeri kullanarak otomatik uygulanan bir özelliğin yedekleme alanına öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="d5cb8-148">Aşağıdaki kod bir `TimeLastLoaded` özellik ekler ve onu seri hale getirilebilir değil olarak işaretler:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="d5cb8-149">Sonraki adım, ödünç uygulama uygulamasına serileştirme kodu eklemektir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="d5cb8-150">Sınıfını seri hale getirmek ve bir dosyaya yazmak için, <xref:System.IO> ve <xref:System.Runtime.Serialization.Formatters.Binary> ad alanlarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="d5cb8-151">Tam nitelikli adları yazmayı önlemek için, aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına başvurular ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="d5cb8-152">Sonraki adım, nesne oluşturulduğunda nesnenin serisini kaldırmak için kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="d5cb8-153">Aşağıdaki kodda gösterildiği gibi serileştirilmiş verilerin dosya adı sınıfına bir sabit ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="d5cb8-154">Sonra, `TestLoan` nesneyi oluşturan satırdan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="d5cb8-155">Önce dosyanın var olduğunu denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-155">You first must check that the file exists.</span></span> <span data-ttu-id="d5cb8-156">Varsa, ikili dosyayı okumak için <xref:System.IO.Stream> bir sınıf ve dosyayı çevirecek bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="d5cb8-157">Akış türünden kredi nesne türüne de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="d5cb8-158">Daha sonra, sınıfı bir dosyaya seri hale getirmek için kod eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="d5cb8-159">`Main` Yöntemdeki mevcut koddan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5cb8-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="d5cb8-160">Bu noktada, uygulamayı derleyip çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="d5cb8-161">İlk kez çalıştırıldığında, faiz oranlarının 7,5 ' de başlayacağını ve sonra 7,1 olarak değiştiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="d5cb8-162">Uygulamayı kapatın ve sonra yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-162">Close the application and then run it again.</span></span> <span data-ttu-id="d5cb8-163">Artık uygulama, kaydedilen dosyayı okudığı iletiyi yazdırır ve faiz oranı, kodu değiştiren koddan önce bile 7,1 olur.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5cb8-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5cb8-164">See also</span></span>

- [<span data-ttu-id="d5cb8-165">Serileştirme (C# )</span><span class="sxs-lookup"><span data-stu-id="d5cb8-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="d5cb8-166">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d5cb8-166">C# Programming Guide</span></span>](../../index.md)
