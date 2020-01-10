---
title: Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma
description: Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturmayı öğrenin
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 9360fccf27a0900d8380461e03baa5806ce1e0da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708924"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Yerelleştirilmiş özel durum iletileriyle Kullanıcı tanımlı özel durumlar oluşturma

Bu makalede, temel <xref:System.Exception> sınıfından devralınan Kullanıcı tanımlı özel durumları, uydu derlemelerini kullanan yerelleştirilmiş özel durum iletileriyle nasıl oluşturacağınızı öğreneceksiniz.

## <a name="create-custom-exceptions"></a>Özel özel durumlar oluşturma

.NET, kullanabileceğiniz birçok farklı özel durum içerir. Ancak, bazı durumlarda, ihtiyaçlarınızı karşılamıyorsa, kendi özel özel durumlarınızı oluşturabilirsiniz.

Bir `StudentName` özelliği içeren `StudentNotFoundException` oluşturmak istediğinizi varsayalım.
Özel bir özel durum oluşturmak için aşağıdaki adımları izleyin:

1. <xref:System.Exception>devralan seri hale getirilebilir bir sınıf oluşturun. Sınıf adı "özel durum" ile bitmelidir:

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
1. Buna yeni bir kaynak dosyası ekleyin. Visual Studio 'da, **Çözüm Gezgini**klasörü üzerinde sağ tıklayın ve > **Yeni öğe** > **kaynaklar dosyası** **Ekle** ' yi seçin. Dosyayı *Exceptionmessages. resx*olarak adlandırın. Bu, varsayılan kaynak dosyasıdır.
1. Aşağıdaki görüntüde gösterildiği gibi, özel durum iletiniz için bir ad/değer çifti ekleyin:

   ![Varsayılan kültüre kaynak ekleme](media/add-resources-to-default-culture.jpg)

1. Fransızca için yeni bir kaynak dosyası ekleyin. *ExceptionMessages.fr-fr. resx*olarak adlandırın.
1. Özel durum iletisi için bir ad/değer çifti ekleyin, ancak bir Fransızca değeri:

   ![Fr-FR kültürüne kaynak ekleme](media/add-resources-to-fr-culture.jpg)

1. Projeyi oluşturduktan sonra, yapı çıkış klasörü, uydu derlemesi olan bir *. dll* dosyası ile *fr-fr* klasörünü içermelidir.
1. Özel durumu aşağıdaki gibi kodla oluşturursunuz:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    > [!NOTE]
    > Proje adı `TestProject` ve *Exceptionmessages. resx* kaynak dosyası projenin *kaynaklar* klasöründe bulunuyorsa, kaynak dosyasının tam adı `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı tanımlı özel durumlar oluşturma](how-to-create-user-defined-exceptions.md)
- [Masaüstü uygulamaları için uydu derlemeleri oluşturma](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [taban (C# başvuru)](../../csharp/language-reference/keywords/base.md)
- [This (C# başvuru)](../../csharp/language-reference/keywords/this.md)
