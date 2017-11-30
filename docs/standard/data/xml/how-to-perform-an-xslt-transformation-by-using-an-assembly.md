---
title: "Nasıl yapılır: bir derlemeyi kullanarak XSLT dönüşümü gerçekleştirin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f236296d604bc465973d17d63883e7b212b7f02d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="b98d6-102">Nasıl yapılır: bir derlemeyi kullanarak XSLT dönüşümü gerçekleştirin</span><span class="sxs-lookup"><span data-stu-id="b98d6-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>
<span data-ttu-id="b98d6-103">XSLT derleyici (xsltc.exe) XSLT stil sayfaları derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b98d6-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="b98d6-104">Derleme doğrudan geçirilen <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b98d6-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="b98d6-105">XML ve XSLT dosyalarını yerel bilgisayarınıza kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="b98d6-105">To copy the XML and XSLT files to your local computer</span></span>  
  
-   <span data-ttu-id="b98d6-106">XSLT dosyasını yerel bilgisayarınıza kopyalayın ve Transform.xsl olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b98d6-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
-   <span data-ttu-id="b98d6-107">XML dosyasını yerel bilgisayarınıza kopyalayın ve adını `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="b98d6-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="b98d6-108">Etkin komut dosyası ile stil sayfası derlemek için.</span><span class="sxs-lookup"><span data-stu-id="b98d6-108">To compile the style sheet with the script enabled.</span></span>  
  
1.  <span data-ttu-id="b98d6-109">Komut satırından şu komutu yürütülürken oluşturur adlı iki derlemeler `Transform.dll` ve `Transform_Script1.dll` (Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="b98d6-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="b98d6-110">Aksi belirtilmediği sürece, sınıf ve derleme adını ana stil sayfasının adı için varsayılan olarak):</span><span class="sxs-lookup"><span data-stu-id="b98d6-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```  
    xsltc /settings:script+ Transform.xsl  
    ```  
  
 <span data-ttu-id="b98d6-111">Aşağıdaki komut, açıkça dönüştürme için sınıf adını ayarlar:</span><span class="sxs-lookup"><span data-stu-id="b98d6-111">The following command explicitly sets the class name to Transform:</span></span>  
  
```  
xsltc /settings:script+ /class:Transform Transform.xsl  
```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="b98d6-112">Kodunuzu derlerken bir başvuru olarak derlenmiş derlemeyi dahil etmek için.</span><span class="sxs-lookup"><span data-stu-id="b98d6-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1.  <span data-ttu-id="b98d6-113">Çözüm Gezgini'nde ya da komut satırından bir başvuru ekleyerek, Visual Studio'da bir derlemeyi dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98d6-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2.  <span data-ttu-id="b98d6-114">C# ile komut satırı için aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="b98d6-114">For the command line with C#, use the following:</span></span>  
  
    ```  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3.  <span data-ttu-id="b98d6-115">Visual Basic komut satırıyla için aşağıdakileri kullanın</span><span class="sxs-lookup"><span data-stu-id="b98d6-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="b98d6-116">Derlenmiş bütünleştirilmiş kodda kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="b98d6-116">To use the compiled assembly in your code.</span></span>  
  
1.  <span data-ttu-id="b98d6-117">Aşağıdaki örnekte nasıl derlenmiş stil sayfasını kullanarak XSLT dönüşümü çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b98d6-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
 [!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
 [!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
 <span data-ttu-id="b98d6-118">Dinamik olarak derlenmiş derlemeye bağlamak için Değiştir</span><span class="sxs-lookup"><span data-stu-id="b98d6-118">To dynamically link to the compiled assembly, replace</span></span>  
  
```  
xslt.Load(typeof(Transform))  
```  
  
 <span data-ttu-id="b98d6-119">örneklerini şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b98d6-119">with</span></span>  
  
```  
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"))  
```  
  
 <span data-ttu-id="b98d6-120">Yukarıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="b98d6-120">in the example above.</span></span> <span data-ttu-id="b98d6-121">Assembly.Load yöntemi hakkında daha fazla bilgi için bkz:<xref:System.Reflection.Assembly.Load%2A></span><span class="sxs-lookup"><span data-stu-id="b98d6-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98d6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b98d6-122">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="b98d6-123">XSLT derleyici (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="b98d6-123">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 [<span data-ttu-id="b98d6-124">XSLT dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="b98d6-124">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="b98d6-125">Komut satırı csc.exe derleme</span><span class="sxs-lookup"><span data-stu-id="b98d6-125">Command-line Building With csc.exe</span></span>](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
