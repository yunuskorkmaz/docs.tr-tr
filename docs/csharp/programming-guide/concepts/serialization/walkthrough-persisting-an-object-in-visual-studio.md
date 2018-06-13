---
title: 'İzlenecek yol: C# kullanarak bir nesneyi kalıcı kılma'
ms.date: 04/26/2018
ms.openlocfilehash: 6c9719dc3aaf997ea144515a553f787450e54041
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956188"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="9a6ec-102">İzlenecek yol: C# kullanarak bir nesneyi kalıcı kılma</span><span class="sxs-lookup"><span data-stu-id="9a6ec-102">Walkthrough: persisting an object using C#</span></span> #

<span data-ttu-id="9a6ec-103">Bir nesnenin veri değerlerini depolamak ve nesne örneği bir sonraki başlatılışında almak sağlar örnekleri arasında kalıcı hale getirmek için seri hale getirme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="9a6ec-104">Bu kılavuzda, temel oluşturacak `Loan` nesne ve verileri bir dosyaya kalır.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="9a6ec-105">Nesne yeniden oluşturduğunuzda, ardından dosyadan verileri alır.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a6ec-106">Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="9a6ec-107">Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulamanın olmalıdır `Create` klasörü için izni.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="9a6ec-108">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="9a6ec-109">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha az izni.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="9a6ec-110">Mümkünse, dağıtım sırasında dosyası oluşturma ve yalnızca izni daha güvenli olan `Read` (yerine bir klasör izinlerini Oluştur) tek bir dosya izni.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="9a6ec-111">Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a6ec-112">Bu örnek verileri bir ikili biçimi dosyasında depolar.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="9a6ec-113">Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas verileri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a6ec-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9a6ec-114">Prerequisites</span></span>

* <span data-ttu-id="9a6ec-115">Derleme ve çalıştırma için yükleme [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="9a6ec-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="9a6ec-116">Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="9a6ec-117">Kod Düzenleyicisi yüklemeniz gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="9a6ec-117">Need to install a code editor?</span></span> <span data-ttu-id="9a6ec-118">Deneyin [Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="9a6ec-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

<span data-ttu-id="9a6ec-119">Örnek kodu çevrimiçi inceleyebilirsiniz [.NET örnekleri GitHub deposunda](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="9a6ec-119">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="9a6ec-120">Kredi nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a6ec-120">Creating the loan object</span></span>

<span data-ttu-id="9a6ec-121">İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir konsol uygulaması:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-121">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="9a6ec-122">Yeni bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-122">Create a new application.</span></span> <span data-ttu-id="9a6ec-123">Tür `dotnet new console -o serialization` adlı bir alt dizinde yeni bir konsol uygulaması oluşturmak için `serialization`.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-123">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="9a6ec-124">Uygulama, düzenleyicisinde açın ve adlı yeni bir sınıf ekleyin `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-124">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="9a6ec-125">Aşağıdaki kodu ekleyin, `Loan` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-125">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="9a6ec-126">Ayrıca kullanan bir uygulama oluşturmanız gerekir `Loan` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-126">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="9a6ec-127">Kredi nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="9a6ec-127">Serialize the loan object</span></span>

1. <span data-ttu-id="9a6ec-128">Açık `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-128">Open `Program.cs`.</span></span> <span data-ttu-id="9a6ec-129">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-129">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="9a6ec-130">Bir olay işleyicisi ekleme `PropertyChanged` olay ve değiştirmek için birkaç satır `Loan` nesne ve değişiklikleri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-130">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="9a6ec-131">Aşağıdaki kodda eklemeleri görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-131">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="9a6ec-132">Bu noktada, kodu çalıştırın ve geçerli çıkış bakın:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-132">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="9a6ec-133">Sürekli olarak her zaman bu uygulamayı çalıştıran aynı değerlere yazar.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-133">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="9a6ec-134">Program çalıştır her zaman yeni bir kredi nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-134">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="9a6ec-135">Gerçek Hayatta, faiz oranları uygulama her çalıştırıldığında düzenli aralıklarla, ancak mutlaka değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-135">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="9a6ec-136">Seri hale getirme kodu uygulama örnekleri arasında en son faiz oranını korumak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-136">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="9a6ec-137">Sonraki adımda, yalnızca serileştirme kredisi sınıfına ekleyerek bunu.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-137">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="9a6ec-138">Nesne kalıcı hale getirmek için seri hale getirme kullanma</span><span class="sxs-lookup"><span data-stu-id="9a6ec-138">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="9a6ec-139">Kredi sınıfı için değerleri kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-139">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="9a6ec-140">Kredi sınıf tanımı üzerinde aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-140">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="9a6ec-141"><xref:System.SerializableAttribute> Derleyici sınıftaki her şeyi bir dosyaya kalıcı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-141">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="9a6ec-142">Çünkü `PropertyChanged` olay depolanması gereken nesne grafiğin parçası temsil etmez, sıralanmamış.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-142">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="9a6ec-143">Bunun yapılması, bu olaya bağlı olan tüm nesneleri seri hale.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-143">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="9a6ec-144">Ekleyebileceğiniz <xref:System.NonSerializedAttribute> için alan bildirimini için `PropertyChanged` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-144">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="9a6ec-145">C# 7.3 ile başlayarak, bir otomatik uygulanan özelliğini kullanarak, yedekleme alanını öznitelikler ekleyebilirsiniz `field` hedef değeri.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-145">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="9a6ec-146">Aşağıdaki kod ekler bir `TimeLastLoaded` özelliği ve getirilemez olarak işaretler:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-146">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="9a6ec-147">Sonraki adım, LoanApp uygulamaya serileştirme kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-147">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="9a6ec-148">Sınıf seri hale getirmek ve bir dosyaya yazmak için kullandığınız <xref:System.IO> ve <xref:System.Runtime.Serialization.Formatters.Binary> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-148">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="9a6ec-149">Tam olarak nitelenmiş adlar yazma zorunluluğunu ortadan kaldırmak için aşağıdaki kodda gösterildiği gibi gerekli ad alanlarına başvurular ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-149">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="9a6ec-150">Sonraki adım, nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-150">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="9a6ec-151">Aşağıdaki kodda gösterildiği gibi serileştirilmiş verilerinin dosya adı için sınıf için bir sabit ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-151">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="9a6ec-152">Ardından, oluşturan satırından sonra aşağıdaki kodu ekleyin `TestLoan` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-152">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="9a6ec-153">İlk dosyanın var olduğunu işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-153">You first must check that the file exists.</span></span> <span data-ttu-id="9a6ec-154">Varsa oluşturma bir <xref:System.IO.Stream> ikili dosya okuma için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-154">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="9a6ec-155">Ayrıca akış türünden kredisi nesne türüne dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-155">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="9a6ec-156">Sonraki sınıfı bir dosyaya serileştirmek için kod eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-156">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="9a6ec-157">Var olan koddan sonra aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="9a6ec-157">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="9a6ec-158">Bu noktada, yeniden yapılandırabilir ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-158">At this point, you can again build and run the application.</span></span> <span data-ttu-id="9a6ec-159">Bunu, ilk çalıştığında faiz oranları 7.5 başlatır ve 7.1 için değişiklikler dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-159">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="9a6ec-160">Uygulamayı kapatın ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-160">Close the application and then run it again.</span></span> <span data-ttu-id="9a6ec-161">Şimdi, uygulama ileti kaydedilen dosya okudu ve hatta değiştiğinde kodundan önce 7.1 faiz oranıdır yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-161">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a6ec-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a6ec-162">See also</span></span>

 [<span data-ttu-id="9a6ec-163">Serileştirme (C# )</span><span class="sxs-lookup"><span data-stu-id="9a6ec-163">Serialization (C# )</span></span>](index.md)  
 [<span data-ttu-id="9a6ec-164">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9a6ec-164">C# Programming Guide</span></span>](../..//index.md)  
