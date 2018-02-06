---
title: "Nasıl yapılır: Office Açık XML belgesi (C#) değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a6bfa60cce332deef2a72da836f96dbe37e65d2a
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2018
---
# <a name="how-to-modify-an-office-open-xml-document-c"></a><span data-ttu-id="cf97e-102">Nasıl yapılır: Office Açık XML belgesi (C#) değiştirme</span><span class="sxs-lookup"><span data-stu-id="cf97e-102">How to: Modify an Office Open XML Document (C#)</span></span>
<span data-ttu-id="cf97e-103">Bu konuda, kaydeder Office Açık XML belge açılır ve değiştirdiği bir örnek sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf97e-103">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="cf97e-104">Office Açık XML hakkında daha fazla bilgi için bkz: [açık XML SDK](https://github.com/OfficeDev/Open-XML-SDK) ve [www.ericwhite.com](http://ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="cf97e-104">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf97e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf97e-105">Example</span></span>  
 <span data-ttu-id="cf97e-106">Bu örnek, belgede ilk paragraf öğesini bulur.</span><span class="sxs-lookup"><span data-stu-id="cf97e-106">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="cf97e-107">Paragrafın metni alır ve ardından siler tüm metni paragrafta çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cf97e-107">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="cf97e-108">Büyük harfe dönüştürülmüş ilk paragraf metni oluşan çalıştırmak bir yeni metin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf97e-108">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="cf97e-109">Open XML pakete değiştirilen XML serileştirir ve kapatılır.</span><span class="sxs-lookup"><span data-stu-id="cf97e-109">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="cf97e-110">Bu örnek WindowsBase derlemesinde sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf97e-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="cf97e-111">Türlerinde kullanan <xref:System.IO.Packaging?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cf97e-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                XDocument xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                PackagePart stylePart = null;  
                XDocument styleDoc = null;  
  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
  
                XElement paraNode = xDoc  
                                    .Root  
                                    .Element(w + "body")  
                                    .Descendants(w + "p")  
                                    .FirstOrDefault();  
  
                string paraText = ParagraphText(paraNode);  
  
                // remove all text runs  
                paraNode.Descendants(w + "r").Remove();  
  
                paraNode.Add(  
                    new XElement(w + "r",  
                        new XElement(w + "t", paraText.ToUpper())  
                    )  
                );  
  
                //  Save the XML into the package  
                using (XmlWriter xw =  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write)))  
                {  
                    xDoc.Save(xw);  
                }  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper());  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cf97e-112">Açarsanız `SampleDoc.docx` bu programını çalıştırdıktan sonra bu program belgede ilk paragrafa büyük harfe dönüştürülmüş görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf97e-112">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="cf97e-113">Bölümünde açıklanan örnek Open XML belgesiyle çalıştırdığınızda [kaynak Office Açık XML belgesi (C#) oluşturulmasını](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="cf97e-113">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf97e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf97e-114">See Also</span></span>  
 [<span data-ttu-id="cf97e-115">Gelişmiş sorgu teknikler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cf97e-115">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
