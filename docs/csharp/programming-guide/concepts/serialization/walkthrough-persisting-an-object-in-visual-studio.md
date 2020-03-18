---
title: 'Walkthrough: C kullanarak bir Nesneyi Kalıcı #'
ms.date: 04/26/2018
ms.openlocfilehash: 85c5d1b711180eda5734d5860d996242c6bc89d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167576"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="375c9-102">Walkthrough: C kullanarak bir nesneyi kalıcı\#</span><span class="sxs-lookup"><span data-stu-id="375c9-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="375c9-103">Bir nesnenin verilerini örnekler arasında kalıcı kılmak için serileştirmeyi kullanabilirsiniz, bu da değerleri depolamanızı ve nesnenin bir sonraki anında elde edildiği nde bunları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="375c9-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="375c9-104">Bu gözden geçirmede, temel `Loan` bir nesne oluşturur ve verilerini bir dosyada devam ettirmeye devam erecektir.</span><span class="sxs-lookup"><span data-stu-id="375c9-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="375c9-105">Nesneyi yeniden oluşturduğunuzda dosyadaki verileri alırsınız.</span><span class="sxs-lookup"><span data-stu-id="375c9-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="375c9-106">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="375c9-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="375c9-107">Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için `Create` izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="375c9-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="375c9-108">İzinler erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="375c9-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="375c9-109">Dosya zaten varsa, uygulamanın `Write` yalnızca izin, daha az izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="375c9-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="375c9-110">Mümkün olduğunda, dosyayı dağıtım sırasında oluşturmak ve yalnızca `Read` tek bir dosyaya izin vermek (klasör için izin oluşturma yerine) daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="375c9-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="375c9-111">Ayrıca, kullanıcı klasörlerine veri yazmak kök klasöre veya Program Dosyaları klasörüne yazmaktan daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="375c9-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="375c9-112">Bu örnek, verileri ikili biçim dosyasında depolar.</span><span class="sxs-lookup"><span data-stu-id="375c9-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="375c9-113">Bu biçimler parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="375c9-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="375c9-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="375c9-114">Prerequisites</span></span>

- <span data-ttu-id="375c9-115">Oluşturmak ve çalıştırmak için [.NET Core SDK'yı](https://dotnet.microsoft.com/download)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="375c9-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="375c9-116">Daha önce yapmadıysanız, en sevdiğiniz kod düzenleyicisini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="375c9-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="375c9-117">Bir kod düzenleyicisi yüklemeniz mi gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="375c9-117">Need to install a code editor?</span></span> <span data-ttu-id="375c9-118">[Visual Studio'yı](https://visualstudio.com/downloads)deneyin!</span><span class="sxs-lookup"><span data-stu-id="375c9-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="375c9-119">Örnek, C# 7.3 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="375c9-119">The example requires C# 7.3.</span></span> <span data-ttu-id="375c9-120">Bkz. [C# dil sürümünü seçin](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="375c9-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="375c9-121">Örnek kodu [.NET örnekleri GitHub deposundan](https://github.com/dotnet/samples/tree/master/csharp/serialization)online olarak inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="375c9-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="375c9-122">Kredi nesnesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="375c9-122">Creating the loan object</span></span>

<span data-ttu-id="375c9-123">İlk adım, sınıfı `Loan` kullanan bir sınıf ve konsol uygulaması oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="375c9-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="375c9-124">Yeni bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="375c9-124">Create a new application.</span></span> <span data-ttu-id="375c9-125">Adlı `dotnet new console -o serialization` `serialization`bir alt dizinde yeni bir konsol uygulaması oluşturmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="375c9-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="375c9-126">Düzenleyicinizde uygulamayı açın ve '' adlı `Loan.cs`yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="375c9-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="375c9-127">Sınıfınıza `Loan` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="375c9-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="375c9-128">Ayrıca sınıfı kullanan bir uygulama oluşturmanız `Loan` gerekir.</span><span class="sxs-lookup"><span data-stu-id="375c9-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="375c9-129">Ödünç nesneyi seri hale</span><span class="sxs-lookup"><span data-stu-id="375c9-129">Serialize the loan object</span></span>

1. <span data-ttu-id="375c9-130">`Program.cs` dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="375c9-130">Open `Program.cs`.</span></span> <span data-ttu-id="375c9-131">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="375c9-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="375c9-132">Olay için bir olay `PropertyChanged` işleyicisi ve `Loan` nesneyi değiştirmek ve değişiklikleri görüntülemek için birkaç satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="375c9-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="375c9-133">Eklemeleri aşağıdaki kodda görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="375c9-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="375c9-134">Bu noktada, kodu çalıştırabilir ve geçerli çıktıyı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="375c9-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="375c9-135">Bu uygulamayı tekrar tekrar çalıştırmak her zaman aynı değerleri yazar.</span><span class="sxs-lookup"><span data-stu-id="375c9-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="375c9-136">Programı her çalıştırdığınızda yeni bir Kredi nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="375c9-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="375c9-137">Gerçek dünyada, faiz oranları periyodik olarak değişir, ancak uygulama çalıştırıldığı her zaman mutlaka değil.</span><span class="sxs-lookup"><span data-stu-id="375c9-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="375c9-138">Serileştirme kodu, uygulama örnekleri arasındaki en son faiz oranını koruduğunuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="375c9-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="375c9-139">Bir sonraki adımda, Kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="375c9-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="375c9-140">Nesneyi Kalıcı Hale Getirmek için Serileştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="375c9-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="375c9-141">Kredi sınıfının değerlerini devam ettirebilmek için, önce sınıfı `Serializable` öznitelikile işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="375c9-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="375c9-142">Kredi sınıfı tanımının üzerine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="375c9-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="375c9-143">Derleyiciye <xref:System.SerializableAttribute> sınıftaki her şeyin bir dosyada kalıcı olarak kalıcı olabileceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="375c9-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="375c9-144">`PropertyChanged` Olay nesne grafiğinin depolanacak bir bölümünü temsil etmediğinden seri hale getirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="375c9-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="375c9-145">Bunu yapmak, bu olaya eklenen tüm nesneleri seri hale getirecektir.</span><span class="sxs-lookup"><span data-stu-id="375c9-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="375c9-146">Olay işleyicisi için alan `PropertyChanged` bildirimine ekleyebilirsiniz. <xref:System.NonSerializedAttribute></span><span class="sxs-lookup"><span data-stu-id="375c9-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="375c9-147">C# 7.3 ile başlayarak, `field` hedef değeri kullanarak otomatik olarak uygulanan bir özelliğin destek alanına öznitelikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="375c9-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="375c9-148">Aşağıdaki kod bir `TimeLastLoaded` özellik ekler ve serileştirilebilir değil olarak işaretler:</span><span class="sxs-lookup"><span data-stu-id="375c9-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="375c9-149">Bir sonraki adım LoanApp uygulamasına serileştirme kodunu eklemektir.</span><span class="sxs-lookup"><span data-stu-id="375c9-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="375c9-150">Sınıfı seri hale getirmek ve bir dosyaya yazmak <xref:System.IO> için, ve <xref:System.Runtime.Serialization.Formatters.Binary> ad boşluklarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="375c9-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="375c9-151">Tam nitelikli adları yazmaktan kaçınmak için, aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına referanslar ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="375c9-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="375c9-152">Bir sonraki adım, nesne oluşturulduğunda dosyadan nesneyi deserialize etmek için kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="375c9-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="375c9-153">Serileştirilmiş verilerin dosya adı için sınıfa aşağıdaki kodda gösterildiği gibi sabit ekleyin:</span><span class="sxs-lookup"><span data-stu-id="375c9-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="375c9-154">Ardından, `TestLoan` nesneyi oluşturan satırdan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="375c9-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="375c9-155">Önce dosyanın var olup olmadığını denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="375c9-155">You first must check that the file exists.</span></span> <span data-ttu-id="375c9-156">Varsa, ikili dosyayı okumak için bir <xref:System.IO.Stream> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıf ve dosyayı çevirmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="375c9-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="375c9-157">Ayrıca akış türünden Kredi nesnetürüne dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="375c9-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="375c9-158">Daha sonra bir dosyaya sınıf serileştirmek için kod eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="375c9-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="375c9-159">`Main` Yöntemde varolan koddan sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="375c9-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="375c9-160">Bu noktada, uygulamayı yeniden oluşturabilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="375c9-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="375c9-161">İlk çalıştığında, faiz oranlarının 7,5'ten başlayıp 7,1'e değiştiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="375c9-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="375c9-162">Uygulamayı kapatın ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="375c9-162">Close the application and then run it again.</span></span> <span data-ttu-id="375c9-163">Şimdi, uygulama kaydedilen dosyayı okuduğu mesajını yazdırır ve faiz oranı, kodu değiştiren koddan önce bile 7,1'dir.</span><span class="sxs-lookup"><span data-stu-id="375c9-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="375c9-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="375c9-164">See also</span></span>

- [<span data-ttu-id="375c9-165">Serileştirme (C# )</span><span class="sxs-lookup"><span data-stu-id="375c9-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="375c9-166">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="375c9-166">C# Programming Guide</span></span>](../..//index.md)
