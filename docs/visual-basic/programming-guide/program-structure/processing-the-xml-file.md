---
title: XML Dosyasını İşleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: ab05db770f312a362e26f17df684f6f4f49c0eb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586742"
---
# <a name="processing-the-xml-file-visual-basic"></a>XML Dosyasını İşleme (Visual Basic)
Derleyici, kodunuzda belgeleri oluşturmak için etiketli her yapı için bir kimlik dizesi oluşturur. (Kodunuzu etiketleme hakkında daha fazla bilgi için bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/index.md).) Kimlik dizesi yapısını benzersiz olarak tanımlar. XML dosyasını işleme programları kimlik dizesi, karşılık gelen .NET Framework meta verileri/yansıma öğeyi tanımlamak için kullanabilirsiniz.  
  
 XML dosyası kodunuzu hiyerarşik bir gösterimini değil; Düz listeyle her öğe için oluşturulan bir kimliği var.  
  
 Kimlik dizeleri oluşturduğunda, derleyici aşağıdaki kurallar gözlemler:  
  
- Hiçbir boşluk dizesinde yerleştirilir.  
  
- Kimlik dizesi ilk bölümünü izleyen iki nokta ile tek bir karakter ile tanımlanmakta üye türünü tanımlar. Aşağıdaki üye türleri kullanılır.  
  
|Karakter|Açıklama|  
|---|---|  
|N|ad alanı<br /><br /> Belge açıklamaları için bir ad alanı ekleyemezsiniz, ancak bunları CREF başvuruları yapabileceğiniz desteklenen durumlarda.|  
|T|Tür: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|alan: `Dim`|  
|P|Özellik: `Property` (varsayılan özellikleri dahil)|  
|M|yöntemi: `Sub`, `Function`, `Declare`, `Operator`|  
|E|olay: `Event`|  
|!|Hata dizesi<br /><br /> Dizenin geri kalanı, hata hakkında bilgi sağlar. Visual Basic Derleyicisi, çözümlenemeyen bağlantılar için hata bilgisi oluşturur.|  
  
- İkinci bölümü `String` tam nitelikli ad alanı kökünde başlangıç öğesi adıdır. Öğesi, kendi kapsayan türleri ve ad alanı adı noktalarla ayrılmış. Öğenin adını nokta içeriyorsa, sayı işaretiyle değiştirilir (#). Öğe adını doğrudan sayı işareti olduğunu kabul edilir. Örneğin, tam olarak nitelenmiş adını `String` Oluşturucusu olacak `System.String.#ctor`.  
  
- Yöntemi için bağımsız değişken varsa özellikleri ve yöntemleri, parantez içindeki bağımsız değişken listesini takip eder. Hiçbir bağımsız değişken varsa, hiçbir parantez yok. Bağımsız değişkenlerin virgülle ayrılır. Her bağımsız değişken kodlama, doğrudan bir .NET Framework imzada nasıl kodlandığını izler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod nasıl kimliği için bir sınıf dizeleri gösterir ve üyelerini oluşturulur.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Nasıl yapılır: XML belgesi oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
