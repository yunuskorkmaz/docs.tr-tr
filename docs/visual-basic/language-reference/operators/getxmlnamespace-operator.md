---
title: "GetXmlNamespace İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace İşleci (Visual Basic)
Alır <xref:System.Xml.Linq.XNamespace> için belirtilen XML ad alanı öneki karşılık gelen nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Bölümler  
 `xmlNamespacePrefix`  
 İsteğe bağlı. XML ad alanı öneki tanımlayan dize. Sağlanan bu dizenin geçerli bir XML tanımlayıcısı olması gerekir. Daha fazla bilgi için bkz: [adları bildirilmiş XML öğeleri ve öznitelikleri](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Önek belirtilmezse, varsayılan ad alanını döndürülür. Varsayılan ad alanı belirtilmezse, boş ad alanı döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Xml.Linq.XNamespace> İçin XML ad alanı öneki karşılık gelen nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetXmlNamespace` İşleci alır <xref:System.Xml.Linq.XNamespace> için XML ad alanı öneki karşılık gelen nesne `xmlNamespacePrefix`.  
  
 XML ad alanı önekleri doğrudan XML değişmez değerleri ve XML eksen özellikleri kullanabilirsiniz. Ancak, kullanmalıdır `GetXmlNamespace` işleci için bir ad alanı öneki dönüştürmek için bir <xref:System.Xml.Linq.XNamespace> kodunuzda kullanabilmeniz için önce nesne. Nitelenmemiş öğe adı için ekleyebilirsiniz bir <xref:System.Xml.Linq.XNamespace> nesnesi tam olarak nitelenmiş <xref:System.Xml.Linq.XName> nesnesi, hangi çok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemleri gerektirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek alır `ns` bir XML ad alanı öneki olarak. XML değişmez değer oluşturmak ve tam adına sahip ilk alt düğüm erişmek için ad alanı öneki sonra kullanan `ns:phone`. Daha sonra bu alt düğüme geçirir `ShowName` kullanarak bir tam ad yapıları alt yordama `GetXmlNamespace` işleci. `ShowName` Alt yordama daha sonra tam adı geçirir <xref:System.Xml.Linq.XNode.Ancestors%2A> üst almak için yöntemi `ns:contact` düğümü.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Çağırdığınızda `TestGetXmlNamespace.RunSample()`, aşağıdaki metni içeren bir ileti kutusu görüntüler:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Visual Basic'de XML'e erişme](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
