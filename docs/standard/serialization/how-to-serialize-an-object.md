---
title: 'Nasıl yapılır: bir nesneyi seri hale getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: 3e24d890d47747c51086214530073fc551321079
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159890"
---
# <a name="how-to-serialize-an-object"></a>Nasıl yapılır: bir nesneyi seri hale getirme
Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun. Bunu yapmak için, XML akışının, akış olarak veya dosya olarak depolanacağı aktarım biçimini belirlemelisiniz. Örneğin, XML akışının kalıcı bir biçimde kaydedilmesi gerekiyorsa <xref:System.IO.FileStream> nesnesi oluşturun.  
  
> [!NOTE]
> XML serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Bir nesneyi serileştirmek için  
  
1. Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.  
  
2. Nesnenin türünü kullanarak bir <xref:System.Xml.Serialization.XmlSerializer> oluşturun. Daha fazla bilgi için <xref:System.Xml.Serialization.XmlSerializer> Sınıf oluşturucuları ' ne bakın.  
  
3. Nesnenin ortak özelliklerinin ve alanlarının bir XML akışını veya bir dosya gösterimini oluşturmak için <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> yöntemini çağırın. Aşağıdaki örnek, bir dosya oluşturur.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
