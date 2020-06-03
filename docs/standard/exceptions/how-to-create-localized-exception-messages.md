---
title: Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma
description: Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturmayı öğrenin
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
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma

Bu makalede, <xref:System.Exception> uydu derlemelerini kullanan yerelleştirilmiş özel durum iletileriyle temel sınıftan devralınan Kullanıcı tanımlı özel durumların nasıl oluşturulacağını öğreneceksiniz.

## <a name="create-custom-exceptions"></a>Özel özel durumlar oluşturma

.NET, kullanabileceğiniz birçok farklı özel durum içerir. Ancak, bazı durumlarda, ihtiyaçlarınızı karşılamıyorsa, kendi özel özel durumlarınızı oluşturabilirsiniz.

Bir özellik içeren bir oluşturmak istediğinizi varsayalım `StudentNotFoundException` `StudentName` .
Özel bir özel durum oluşturmak için aşağıdaki adımları izleyin:

1. Öğesinden devralan seri hale getirilebilir bir sınıf oluşturun <xref:System.Exception> . Sınıf adı "özel durum" ile bitmelidir:

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

Özel bir özel durum oluşturdunuz ve aşağıdaki gibi kodla dilediğiniz yerde oluşturabilirsiniz:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Önceki satırla ilgili sorun `"The student cannot be found."` yalnızca sabit bir dizedir. Yerelleştirilmiş bir uygulamada, Kullanıcı kültürüne bağlı olarak farklı iletilere sahip olmak istersiniz.
[Uydu derlemeleri](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) bunu yapmanın iyi bir yoludur. Uydu derlemesi, belirli bir dilin kaynaklarını içeren bir. dll ' dir. Çalışma zamanında belirli bir kaynak istediğinizde, CLR bu kaynağı Kullanıcı kültürüne göre bulur. Bu kültür için uydu bütünleştirilmiş kodu bulunmazsa, varsayılan kültürün kaynakları kullanılır.

Yerelleştirilmiş özel durum iletilerini oluşturmak için:

1. Kaynak dosyalarını tutmak için *kaynaklar* adlı yeni bir klasör oluşturun.
1. Buna yeni bir kaynak dosyası ekleyin. Visual Studio 'da, **Çözüm Gezgini**klasörü üzerinde sağ tıklayın ve **Add**  >  **Yeni öğe**  >  **kaynakları dosyası**Ekle ' yi seçin. Dosyayı *Exceptionmessages. resx*olarak adlandırın. Bu, varsayılan kaynak dosyasıdır.
1. Aşağıdaki görüntüde gösterildiği gibi, özel durum iletiniz için bir ad/değer çifti ekleyin:

   ![Varsayılan kültüre kaynak ekleme](media/add-resources-to-default-culture.jpg)

1. Fransızca için yeni bir kaynak dosyası ekleyin. *ExceptionMessages.fr-fr. resx*olarak adlandırın.
1. Özel durum iletisi için bir ad/değer çifti ekleyin, ancak bir Fransızca değeri:

   ![Fr-FR kültürüne kaynak ekleme](media/add-resources-to-fr-culture.jpg)

1. Projeyi oluşturduktan sonra, yapı çıkış klasörü, uydu derlemesi olan bir *. dll* dosyası ile *fr-fr* klasörünü içermelidir.
1. Özel durumu aşağıdaki gibi kodla oluşturursunuz:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Proje adı ise `TestProject` ve *exceptionmessages. resx* kaynak dosyası projenin *kaynaklar* klasöründe bulunuyorsa, kaynak dosyasının tam adı olur `TestProject.Resources.ExceptionMessages` .

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md)
- [Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# Başvurusu)](../../csharp/language-reference/keywords/base.md)
- [this (C# Başvurusu)](../../csharp/language-reference/keywords/this.md)
