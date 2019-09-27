---
title: 'Nasıl yapılır: yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma'
description: Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturmayı öğrenin
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332993"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="25bef-103">Nasıl yapılır: yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="25bef-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="25bef-104">Bu makalede, uydu derlemelerini kullanan yerelleştirilmiş özel durum iletileriyle temel <xref:System.Exception> sınıfından devralınan Kullanıcı tanımlı özel durumlar oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="25bef-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="25bef-105">Özel özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="25bef-105">Create custom exceptions</span></span>

<span data-ttu-id="25bef-106">.NET, kullanabileceğiniz birçok farklı özel durum içerir.</span><span class="sxs-lookup"><span data-stu-id="25bef-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="25bef-107">Ancak, bazı durumlarda, ihtiyaçlarınızı karşılamıyorsa, kendi özel özel durumlarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25bef-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="25bef-108">Bir `StudentName` özelliği içeren `StudentNotFoundException` oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="25bef-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="25bef-109">Özel bir özel durum oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="25bef-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="25bef-110">@No__t-0 ' dan devralan seri hale getirilebilir bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="25bef-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="25bef-111">Sınıf adı "özel durum" ile bitmelidir:</span><span class="sxs-lookup"><span data-stu-id="25bef-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="25bef-112">Varsayılan oluşturucuları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="25bef-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

1. <span data-ttu-id="25bef-113">Ek özellikleri ve oluşturucuları tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="25bef-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="25bef-114">Yerelleştirilmiş özel durum iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="25bef-114">Create localized exception messages</span></span>

<span data-ttu-id="25bef-115">Özel bir özel durum oluşturdunuz ve aşağıdaki gibi kodla dilediğiniz yerde oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25bef-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="25bef-116">Önceki satırla ilgili sorun "öğrenci bulunamıyor" olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="25bef-116">The problem with the previous line is that "The student cannot be found."</span></span> <span data-ttu-id="25bef-117">yalnızca sabit bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="25bef-117">is just a constant string.</span></span> <span data-ttu-id="25bef-118">Yerelleştirilmiş bir uygulamada, Kullanıcı kültürüne bağlı olarak farklı iletilere sahip olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="25bef-118">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="25bef-119">[Uydu derlemeleri](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) bunu yapmanın iyi bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="25bef-119">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="25bef-120">Uydu derlemesi, belirli bir dilin kaynaklarını içeren bir. dll ' dir.</span><span class="sxs-lookup"><span data-stu-id="25bef-120">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="25bef-121">Çalışma zamanında belirli bir kaynak istediğinizde, CLR bu kaynağı Kullanıcı kültürüne göre bulur.</span><span class="sxs-lookup"><span data-stu-id="25bef-121">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="25bef-122">Bu kültür için uydu bütünleştirilmiş kodu bulunmazsa, varsayılan kültürün kaynakları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25bef-122">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="25bef-123">Yerelleştirilmiş özel durum iletilerini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="25bef-123">To create the localized exception messages:</span></span>

1. <span data-ttu-id="25bef-124">Kaynak dosyalarını tutmak için *kaynaklar* adlı yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="25bef-124">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="25bef-125">Buna yeni bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25bef-125">Add a new resource file to it.</span></span> <span data-ttu-id="25bef-126">Visual Studio 'da, **Çözüm Gezgini**klasörü üzerinde sağ tıklayın ve  -> **Yeni öğe** -> **kaynak dosyası** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="25bef-126">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** -> **New Item** -> **Resources File**.</span></span> <span data-ttu-id="25bef-127">Dosyayı *Exceptionmessages. resx*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="25bef-127">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="25bef-128">Bu, varsayılan kaynak dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="25bef-128">This is the default resources file.</span></span>
1. <span data-ttu-id="25bef-129">Aşağıdaki görüntüde gösterildiği gibi, özel durum iletiniz için bir ad/değer çifti ekleyin: ![ varsayılan kültüre kaynak ekleyin @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="25bef-129">Add a name/value pair for your exception message, like the following image shows: ![Add resources to the default culture](media/add-resources-to-default-culture.jpg)</span></span>
1. <span data-ttu-id="25bef-130">Fransızca için yeni bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25bef-130">Add a new resource file for French.</span></span> <span data-ttu-id="25bef-131">*ExceptionMessages.fr-fr. resx*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="25bef-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="25bef-132">Özel durum iletisi için bir ad/değer çifti ekleyin, ancak bir Fransızca değeri: ![Fr-FR kültürü @ no__t-1 ' e kaynak ekleme</span><span class="sxs-lookup"><span data-stu-id="25bef-132">Add a name/value pair for the exception message again, but with a French value: ![Add resources to the fr-FR culture](media/add-resources-to-fr-culture.jpg)</span></span>
1. <span data-ttu-id="25bef-133">Projeyi oluşturduktan sonra, yapı çıkış klasörü, uydu derlemesi olan bir *. dll* dosyası ile *fr-fr* klasörünü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="25bef-133">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="25bef-134">Özel durumu aşağıdaki gibi kodla oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="25bef-134">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="25bef-135">Proje adı `TestProject` ise ve *Exceptionmessages. resx* kaynak dosyası projenin *kaynaklar* klasöründe bulunuyorsa, kaynak dosyasının tam adı `TestProject.Resources.ExceptionMessages` ' dir.</span><span class="sxs-lookup"><span data-stu-id="25bef-135">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="25bef-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25bef-136">See also</span></span>

- [<span data-ttu-id="25bef-137">Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="25bef-137">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="25bef-138">Masaüstü uygulamaları için uydu derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="25bef-138">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="25bef-139">taban (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="25bef-139">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="25bef-140">This (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="25bef-140">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
