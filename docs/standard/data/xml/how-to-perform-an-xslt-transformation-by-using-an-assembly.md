---
title: 'Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
ms.openlocfilehash: 623f997d1c11bc643ea4605614cac147b6069be5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287733"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a>Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme
XSLT derleyicisi (xsltc. exe) XSLT stil sayfalarını derler ve bir derleme oluşturur. Derleme doğrudan <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a>XML ve XSLT dosyalarını yerel bilgisayarınıza kopyalamak için  
  
- XSLT dosyasını yerel bilgisayarınıza kopyalayın ve Transform. xsl olarak adlandırın.  
  
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
  
- XML dosyasını yerel bilgisayarınıza kopyalayın ve adlandırın `books.xml` .  
  
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
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a>Komut dosyası etkinken stil sayfasını derlemek için.  
  
1. Komut satırından aşağıdaki komutu yürütmek, ve adlı iki derleme oluşturur `Transform.dll` `Transform_Script1.dll` (Bu, varsayılan davranıştır. Aksi belirtilmedikçe, sınıfın adı ve derleme varsayılan olarak ana stil sayfasının adını alır):  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    Aşağıdaki komut, sınıf adını dönüştürmek için açıkça ayarlar:  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a>Kodunuzu derlerken derlenmiş derlemeyi başvuru olarak eklemek için.  
  
1. Çözüm Gezgini veya komut satırından bir başvuru ekleyerek Visual Studio 'da bir derlemeyi dahil edebilirsiniz.  
  
2. C# ile komut satırı için aşağıdakileri kullanın:  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. Visual Basic olan komut satırı için aşağıdakini kullanın  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a>Kodunuzda derlenen derlemeyi kullanmak için.  
  
Aşağıdaki örnek, derlenmiş stil sayfasını kullanarak XSLT dönüşümünün nasıl yürütüleceğini gösterir.  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
Derlenmiş derlemeye dinamik olarak bağlanmak için, Değiştir
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
örneklerini şununla değiştirin:  
  
```csharp
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
```
  
Yukarıdaki örnekte. Assembly. Load yöntemi hakkında daha fazla bilgi için bkz <xref:System.Reflection.Assembly.Load%2A> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [XSLT Derleyicisi (xsltc.exe)](xslt-compiler-xsltc-exe.md)
- [XSLT Dönüşümleri](xslt-transformations.md)
- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
