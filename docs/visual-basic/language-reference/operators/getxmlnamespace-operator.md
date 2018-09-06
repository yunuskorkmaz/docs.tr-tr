---
title: GetXmlNamespace İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: e21cf160d10f308990894d1a85c4f5d05b90f68d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786615"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace İşleci (Visual Basic)
Alır <xref:System.Xml.Linq.XNamespace> belirtilen XML ad alanı öneki için karşılık gelen nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Bölümler  
 `xmlNamespacePrefix`  
 İsteğe bağlı. XML ad alanı öneki tanımlayan dize. Belirtilirse, bu dizenin geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için [adları, bildirilmiş XML öğeleri ve özniteliklerinin](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Önek yok belirtilirse, varsayılan ad alanı döndürülür. Boş ad alanı varsayılan ad alanı yok belirtilirse, döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Xml.Linq.XNamespace> XML ad alanı öneki için karşılık gelen nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetXmlNamespace` İşleci alır <xref:System.Xml.Linq.XNamespace> XML ad alanı öneki için karşılık gelen nesne `xmlNamespacePrefix`.  
  
 XML ad alanı öneklerini doğrudan XML sabit değerleri ve XML eksen özellikleri de kullanabilirsiniz. Ancak, kullanmalısınız `GetXmlNamespace` işleci için bir ad alanı öneki dönüştürmek için bir <xref:System.Xml.Linq.XNamespace> kodunuzda kullanmadan önce nesne. Bir nitelenmemiş öğe adı için eklediğiniz bir <xref:System.Xml.Linq.XNamespace> tam alınacak nesne <xref:System.Xml.Linq.XName> nesnesi, hangi çok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemleri gerektirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek alır `ns` olarak bir XML ad alanı öneki. XML değişmez değer oluşturmak ve bir nitelenmiş ada sahip ilk alt düğüm erişmek için bir ad alanı öneki kullanır `ns:phone`. Daha sonra bu alt düğüme geçirir `ShowName` kullanarak tam bir ad oluşturur alt yordam `GetXmlNamespace` işleci. `ShowName` Alt yordam daha sonra tam adı için geçirir <xref:System.Xml.Linq.XNode.Ancestors%2A> üst almak için yöntemi `ns:contact` düğümü.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Çağırdığınızda `TestGetXmlNamespace.RunSample()`, aşağıdaki metni içeren bir ileti kutusu görüntüler:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Visual Basic'de XML'e erişme](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
