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
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Yerelleştirilmiş özel durum iletileriyle kullanıcı tanımlı özel durumlar oluşturma

Bu makalede, uydu derlemelerini kullanarak yerelleştirilmiş özel durum iletileriyle <xref:System.Exception> taban sınıftan devralınan kullanıcı tanımlı özel durumlar oluşturmayı öğreneceksiniz.

## <a name="create-custom-exceptions"></a>Özel özel durumlar oluşturma

.NET kullanabileceğiniz birçok farklı özel durum içerir. Ancak, bazı durumlarda bunların hiçbiri gereksinimlerinizi karşılamadığında, kendi özel özel durumlarınızı oluşturabilirsiniz.

Bir özellik içeren bir `StudentNotFoundException` `StudentName` özellik oluşturmak istediğinizi varsayalım.
Özel bir özel durum oluşturmak için aşağıdaki adımları izleyin:

1. 'den <xref:System.Exception>devralınan bir serileştirilebilir sınıf oluşturun Sınıf adı "Özel Durum" ile bitmelidir:

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

1. Varsayılan oluşturucuları ekleyin:

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

1. Ek özellikleri ve oluşturucuları tanımlayın:

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

## <a name="create-localized-exception-messages"></a>Yerelleştirilmiş özel durum iletileri oluşturma

Özel bir özel durum oluşturdunuz ve aşağıdaki gibi kodla her yere atabilirsiniz:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Önceki satır ile sorun `"The student cannot be found."` sadece sabit bir dize olmasıdır. Yerelleştirilmiş bir uygulamada, kullanıcı kültürüne bağlı olarak farklı iletilere sahip olmak istersiniz.
[Uydu Meclisleri](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) bunu yapmak için iyi bir yoldur. Uydu derlemesi, belirli bir dil için kaynak içeren bir .dll'dir. Çalışma zamanında belirli bir kaynak istediğinizde, CLR bu kaynağı kullanıcı kültürüne bağlı olarak bulur. Bu kültür için uydu derlemesi bulunmazsa, varsayılan kültürün kaynakları kullanılır.

Yerelleştirilmiş özel durum iletileri oluşturmak için:

1. Kaynak dosyalarını tutmak için *Kaynaklar* adlı yeni bir klasör oluşturun.
1. Yeni bir kaynak dosyası ekleyin. Visual Studio'da bunu yapmak için **Solution Explorer'daki**klasöre sağ tıklayın ve**Yeni Öğe** > **Kaynakları Dosyası** **Ekle'yi** > seçin. Dosyayı *adlandırın ExceptionMessages.resx*. Bu varsayılan kaynaklar dosyasıdır.
1. Aşağıdaki resimdeki gibi özel durum iletiniz için bir ad/değer çifti ekleyin:

   ![Varsayılan kültüre kaynak ekleme](media/add-resources-to-default-culture.jpg)

1. Fransızca için yeni bir kaynak dosyası ekleyin. Adını *ExceptionMessages.fr-FR.resx.*
1. Özel durum iletisi için yine bir ad/değer çifti ekleyin, ancak Fransızca değeri ile:

   ![FR-FR kültürüne kaynak ekleme](media/add-resources-to-fr-culture.jpg)

1. Projeyi yaptıktan sonra, yapı çıktısı klasörü uydu derlemesi olan *.dll* dosyasına sahip *fr-FR* klasörünü içermelidir.
1. Aşağıdaki gibi kod ile özel durum atmak:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Proje adı ysa `TestProject` ve kaynak dosyası *ExceptionMessages.resx* projenin *Kaynaklar* klasöründe bulunursa, kaynak dosyasının tam nitelikli adı . `TestProject.Resources.ExceptionMessages`

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı tanımlı özel durumlar nasıl oluşturulur?](how-to-create-user-defined-exceptions.md)
- [Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# Başvurusu)](../../csharp/language-reference/keywords/base.md)
- [this (C# Başvurusu)](../../csharp/language-reference/keywords/this.md)
