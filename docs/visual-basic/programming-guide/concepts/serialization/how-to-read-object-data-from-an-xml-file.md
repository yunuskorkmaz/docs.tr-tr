---
title: "Nasıl yapılır: nesne verilerini bir XML dosyasından (Visual Basic) okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="3537f-102">Nasıl yapılır: nesne verilerini bir XML dosyasından (Visual Basic) okuma</span><span class="sxs-lookup"><span data-stu-id="3537f-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="3537f-103">Bu örnek daha önce bir XML dosyası kullanmaya yazıldı nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3537f-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3537f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3537f-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3537f-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3537f-105">Compiling the Code</span></span>  
 <span data-ttu-id="3537f-106">Dosya adı "c:\temp\SerializationOverview.xml" serileştirilmiş verilerini içeren dosyanın adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3537f-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="3537f-107">Verileri seri hale getirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesne verilerini bir XML dosyasına (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="3537f-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="3537f-108">Sınıf parametresiz ortak bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3537f-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="3537f-109">Yalnızca genel özellikleri ve alanları serisi.</span><span class="sxs-lookup"><span data-stu-id="3537f-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3537f-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3537f-110">Robust Programming</span></span>  
 <span data-ttu-id="3537f-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="3537f-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3537f-112">Serileştirilen sınıfı genel, parametresiz bir oluşturucu yok.</span><span class="sxs-lookup"><span data-stu-id="3537f-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="3537f-113">Veri dosyasındaki verileri seri durumdan çıkarılacak sınıfından temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="3537f-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="3537f-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3537f-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3537f-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3537f-115">.NET Framework Security</span></span>  
 <span data-ttu-id="3537f-116">Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan veri serisi.</span><span class="sxs-lookup"><span data-stu-id="3537f-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="3537f-117">Yeniden oluşturulan nesne, seri durumdan kod izinleriyle yerel bir bilgisayarda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3537f-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="3537f-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="3537f-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3537f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3537f-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="3537f-120">Nasıl yapılır: nesne verilerini bir XML dosyası (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="3537f-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="3537f-121">Seri hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3537f-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="3537f-122">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3537f-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
