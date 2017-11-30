---
title: "Nasıl yapılır: nesne verilerini bir XML dosyası (Visual Basic) yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df461f9b560dac45add0d7c82ff4938b0a7b1e62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="60e0b-102">Nasıl yapılır: nesne verilerini bir XML dosyası (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="60e0b-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="60e0b-103">Bu örnek, bir XML dosyası kullanarak bir sınıftan nesne Yazar <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="60e0b-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60e0b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="60e0b-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60e0b-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="60e0b-105">Compiling the Code</span></span>  
 <span data-ttu-id="60e0b-106">Sınıf parametresiz ortak bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60e0b-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="60e0b-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="60e0b-107">Robust Programming</span></span>  
 <span data-ttu-id="60e0b-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="60e0b-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="60e0b-109">Serileştirilen sınıfı genel, parametresiz bir oluşturucu yok.</span><span class="sxs-lookup"><span data-stu-id="60e0b-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="60e0b-110">Dosya var ve salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="60e0b-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="60e0b-111">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="60e0b-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="60e0b-112">Disk dolu olduğundan (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="60e0b-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="60e0b-113">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="60e0b-113">.NET Framework Security</span></span>  
 <span data-ttu-id="60e0b-114">Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60e0b-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="60e0b-115">Bir uygulama bir dosya oluşturmak gerekirse, bu uygulamanın ihtiyacı `Create` klasörü için erişim.</span><span class="sxs-lookup"><span data-stu-id="60e0b-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="60e0b-116">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişimi, daha düşük ayrıcalık.</span><span class="sxs-lookup"><span data-stu-id="60e0b-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="60e0b-117">Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca izni için daha güvenli olan `Read` tek bir dosyaya erişim yerine `Create` bir klasör için erişim.</span><span class="sxs-lookup"><span data-stu-id="60e0b-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e0b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60e0b-118">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="60e0b-119">Nasıl yapılır: nesne verilerini bir XML dosyasından (Visual Basic) okuma</span><span class="sxs-lookup"><span data-stu-id="60e0b-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="60e0b-120">Seri hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60e0b-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
