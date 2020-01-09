---
title: XmlSerializer kullanarak bir nesne serisini kaldırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c24ba466a208fe5abdbf565169c41c4ee3f47482
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559904"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a>XmlSerializer kullanarak bir nesne serisini kaldırma

Bir nesnenin serisini kaldırdığınızda, aktarım biçimi bir akış veya dosya nesnesi oluşturup oluşturamayacağını belirler. Aktarım biçimi saptandıktan sonra, gerektiğinde <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> veya <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> yöntemlerini çağırabilirsiniz.

## <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için

1. Seri durumdan çıkarılacak nesnenin türünü kullanarak bir <xref:System.Xml.Serialization.XmlSerializer> oluşturun.

1. Arama <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> nesnenin bir kopyasını oluşturmak için yöntemi. Seri durumdan çıkarma sırasında döndürülen nesneyi, aşağıdaki örnekte gösterildiği gibi, bir dosyanın bir dosyadan serileştirerek (bir akıştan seri durumdan çıkarılabilse de), bu nesnenin özgün türüne atamalısınız.

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Serileştirmeye Giriş](introducing-xml-serialization.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
