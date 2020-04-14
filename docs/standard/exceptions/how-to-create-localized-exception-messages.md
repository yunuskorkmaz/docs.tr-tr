---
title: Yerelleştirilmiş özel durum iletileriyle kullanıcı tanımlı özel durumlar oluşturma
description: Yerelleştirilmiş özel durum iletileriyle kullanıcı tanımlı özel durumlar oluşturmayı öğrenin
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243355"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="c4af4-103">Yerelleştirilmiş özel durum iletileriyle kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4af4-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="c4af4-104">Bu makalede, uydu derlemelerini kullanarak yerelleştirilmiş özel durum iletileriyle <xref:System.Exception> taban sınıftan devralınan kullanıcı tanımlı özel durumlar oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c4af4-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="c4af4-105">Özel özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4af4-105">Create custom exceptions</span></span>

<span data-ttu-id="c4af4-106">.NET kullanabileceğiniz birçok farklı özel durum içerir.</span><span class="sxs-lookup"><span data-stu-id="c4af4-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="c4af4-107">Ancak, bazı durumlarda bunların hiçbiri gereksinimlerinizi karşılamadığında, kendi özel özel durumlarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4af4-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="c4af4-108">Bir özellik içeren bir `StudentNotFoundException` `StudentName` özellik oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4af4-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="c4af4-109">Özel bir özel durum oluşturmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c4af4-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="c4af4-110">'den <xref:System.Exception>devralınan bir serileştirilebilir sınıf oluşturun</span><span class="sxs-lookup"><span data-stu-id="c4af4-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="c4af4-111">Sınıf adı "Özel Durum" ile bitmelidir:</span><span class="sxs-lookup"><span data-stu-id="c4af4-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="c4af4-112">Varsayılan oluşturucuları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4af4-112">Add the default constructors:</span></span>

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

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="c4af4-113">Ek özellikleri ve oluşturucuları tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="c4af4-113">Define any additional properties and constructors:</span></span>

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

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="c4af4-114">Yerelleştirilmiş özel durum iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4af4-114">Create localized exception messages</span></span>

<span data-ttu-id="c4af4-115">Özel bir özel durum oluşturdunuz ve aşağıdaki gibi kodla her yere atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4af4-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="c4af4-116">Önceki satır ile sorun `"The student cannot be found."` sadece sabit bir dize olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c4af4-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="c4af4-117">Yerelleştirilmiş bir uygulamada, kullanıcı kültürüne bağlı olarak farklı iletilere sahip olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="c4af4-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="c4af4-118">[Uydu Meclisleri](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) bunu yapmak için iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="c4af4-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="c4af4-119">Uydu derlemesi, belirli bir dil için kaynak içeren bir .dll'dir.</span><span class="sxs-lookup"><span data-stu-id="c4af4-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="c4af4-120">Çalışma zamanında belirli bir kaynak istediğinizde, CLR bu kaynağı kullanıcı kültürüne bağlı olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="c4af4-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="c4af4-121">Bu kültür için uydu derlemesi bulunmazsa, varsayılan kültürün kaynakları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4af4-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="c4af4-122">Yerelleştirilmiş özel durum iletileri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="c4af4-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="c4af4-123">Kaynak dosyalarını tutmak için *Kaynaklar* adlı yeni bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4af4-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="c4af4-124">Yeni bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4af4-124">Add a new resource file to it.</span></span> <span data-ttu-id="c4af4-125">Visual Studio'da bunu yapmak için **Solution Explorer'daki**klasöre sağ tıklayın ve**Yeni Öğe** > **Kaynakları Dosyası** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="c4af4-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="c4af4-126">Dosyayı *adlandırın ExceptionMessages.resx*.</span><span class="sxs-lookup"><span data-stu-id="c4af4-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="c4af4-127">Bu varsayılan kaynaklar dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c4af4-127">This is the default resources file.</span></span>
1. <span data-ttu-id="c4af4-128">Aşağıdaki resimdeki gibi özel durum iletiniz için bir ad/değer çifti ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4af4-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Varsayılan kültüre kaynak ekleme](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="c4af4-130">Fransızca için yeni bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4af4-130">Add a new resource file for French.</span></span> <span data-ttu-id="c4af4-131">Adını *ExceptionMessages.fr-FR.resx.*</span><span class="sxs-lookup"><span data-stu-id="c4af4-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="c4af4-132">Özel durum iletisi için yine bir ad/değer çifti ekleyin, ancak Fransızca değeri ile:</span><span class="sxs-lookup"><span data-stu-id="c4af4-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![FR-FR kültürüne kaynak ekleme](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="c4af4-134">Projeyi yaptıktan sonra, yapı çıktısı klasörü uydu derlemesi olan *.dll* dosyasına sahip *fr-FR* klasörünü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c4af4-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="c4af4-135">Aşağıdaki gibi kod ile özel durum atmak:</span><span class="sxs-lookup"><span data-stu-id="c4af4-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="c4af4-136">Proje adı ysa `TestProject` ve kaynak dosyası *ExceptionMessages.resx* projenin *Kaynaklar* klasöründe bulunursa, kaynak dosyasının tam nitelikli adı . `TestProject.Resources.ExceptionMessages`</span><span class="sxs-lookup"><span data-stu-id="c4af4-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4af4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4af4-137">See also</span></span>

- [<span data-ttu-id="c4af4-138">Kullanıcı tanımlı özel durumlar nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="c4af4-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="c4af4-139">Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4af4-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="c4af4-140">base (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4af4-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="c4af4-141">this (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4af4-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
