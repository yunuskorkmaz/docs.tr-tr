---
title: XML Dosyasını İşleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 6be7597f1c03d8aa044eba70ef6287cfc07d9b84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="processing-the-xml-file-visual-basic"></a>XML Dosyasını İşleme (Visual Basic)
Derleyici kodunuzda belgeleri oluşturmak için etiketli her yapı için bir kimlik dizesi oluşturur. (Kodunuzu etiketi hakkında daha fazla bilgi için bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) Kimlik dizesi, yapı benzersiz olarak tanımlar. XML dosyasını işleme programlar karşılık gelen tanımlamak için bir kimlik dizesi kullanabilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] meta veri/yansıma öğesi.  
  
 XML dosyası kodunuzu hiyerarşik bir gösterimini değil; her öğe için oluşturulan kimliği düz bir listesidir.  
  
 Kimlik dizeleri oluşturduğunda derleyici aşağıdaki kurallara uyan:  
  
-   Hiçbir boşluk dizesi içinde yer alır.  
  
-   Kimlik dizesi ilk bölümü, izleyen iki nokta ile tek bir karakter ile tanımlanmasını üye türünü tanımlar. Aşağıdaki üye türleri kullanılır.  
  
|Karakter|Açıklama|  
|---|---|  
|N|ad alanı<br /><br /> Belge açıklamaları için bir ad alanı ekleyemezsiniz, ancak bunları CREF başvurular yapabilirsiniz desteklendiği yerlerde.|  
|T|Tür: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|alan: `Dim`|  
|P|Özellik: `Property` (varsayılan özellikleri dahil)|  
|M|yöntem: `Sub`, `Function`, `Declare`, `Operator`|  
|E|Olay: `Event`|  
|!|Hata dizesi<br /><br /> Dizenin geri kalanı hata hakkında bilgi sağlar. Visual Basic derleyici çözümlenemiyor bağlantılar için hata bilgilerini oluşturur.|  
  
-   İkinci bölümü `String` ad alanı kökünde başlayan öğesi, tam adı. Öğesi, kendi kapsayan türlerini ve ad alanı adını noktalarla ayrılmış. Öğesinin adı nokta içeriyorsa, numara karakteriyle değiştirilir (#). Öğe adını doğrudan bir numara işareti olduğunu varsayılır. Örneğin, tam adını `String` Oluşturucusu olacaktır `System.String.#ctor`.  
  
-   Yöntemi için bağımsız değişkeni varsa özellikleri ve yöntemleri için ayraç içinde bağımsız değişken listesi aşağıdadır. Bağımsız değişkenler varsa, hiçbir parantez yok. Bağımsız değişkenler virgülle ayrılır. Her bağımsız değişkeni kodlama doğrudan nasıl içinde kodlanır izleyen bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] imza.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kimliği için bir sınıf nasıl dizeleri gösterir ve üyeleri üretilir.  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
