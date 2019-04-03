---
title: 'Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: f6233fc7ce74cbd39237bab07cfd2ed22b9c2240
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834900"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="39d9c-102">Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d9c-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="39d9c-103">Bu örnek daha önce bir XML dosyası kullanmayı yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="39d9c-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39d9c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="39d9c-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="39d9c-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="39d9c-105">Compiling the Code</span></span>  
 <span data-ttu-id="39d9c-106">Dosya adı "c:\temp\SerializationOverview.xml" seri hale getirilmiş veri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="39d9c-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="39d9c-107">Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="39d9c-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="39d9c-108">Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39d9c-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="39d9c-109">Yalnızca ortak özellikler ve alanları seri.</span><span class="sxs-lookup"><span data-stu-id="39d9c-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="39d9c-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="39d9c-110">Robust Programming</span></span>  
 <span data-ttu-id="39d9c-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="39d9c-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="39d9c-112">Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="39d9c-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="39d9c-113">Dosyasındaki verilerin veri seri durumdan sınıftan temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="39d9c-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="39d9c-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="39d9c-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="39d9c-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="39d9c-115">.NET Framework Security</span></span>  
 <span data-ttu-id="39d9c-116">Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan gelen verileri seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="39d9c-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="39d9c-117">Yeniden oluşturulan nesne, seri durumdan kodun izinlere sahip bir yerel bilgisayarda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="39d9c-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="39d9c-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="39d9c-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d9c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39d9c-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="39d9c-120">Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="39d9c-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="39d9c-121">Seri hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d9c-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="39d9c-122">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="39d9c-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
