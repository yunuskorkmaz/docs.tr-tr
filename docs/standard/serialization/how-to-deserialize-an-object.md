---
title: XmlSerializer kullanarak bir nesne serisini kaldırma
description: Bir nesnenin serisini kaldırma hakkında bilgi edinin. Aktarım biçimi, bir akış veya dosya nesnesi oluşturulup oluşturulmayacağını belirler.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c0fb5b2206251d880618a68e5cdb2db2b19c57da
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259518"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a>XmlSerializer kullanarak bir nesne serisini kaldırma

Bir nesnenin serisini kaldırdığınızda, aktarım biçimi bir akış veya dosya nesnesi oluşturup oluşturamayacağını belirler. Aktarım biçimi saptandıktan sonra, <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> veya <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> yöntemlerini gerektiği şekilde çağırabilirsiniz.

## <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için

1. <xref:System.Xml.Serialization.XmlSerializer>Seri durumdan çıkarılacak nesnenin türünü kullanarak oluşturun.

1. Arama <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> nesnenin bir kopyasını oluşturmak için yöntemi. Seri durumdan çıkarma sırasında döndürülen nesneyi, aşağıdaki örnekte gösterildiği gibi, bir dosyanın bir dosyadan serileştirerek (bir akıştan seri durumdan çıkarılabilse de), bu nesnenin özgün türüne atamalısınız.

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Using myFileStream As New FileStream("myFileName.xml", FileMode.Open)
        ' Call the Deserialize method and cast to the object type.
        Dim myObject = CType( _
             mySerializer.Deserialize(myFileStream), MySerializableClass)
     End Using
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    using var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass)mySerializer.Deserialize(myFileStream);
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Serileştirmeye Giriş](introducing-xml-serialization.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
