---
title: Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
ms.openlocfilehash: 4a53ba4fe16a3653b1be380da49e6b75cb347a28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710680"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme
Belgedeki düğümleri ve içerikleri değiştirebileceğiniz birçok yol vardır. Şunları yapabilirsiniz:  
  
- <xref:System.Xml.XmlNode.Value%2A> özelliğini kullanarak düğümlerin değerini değiştirin.  
  
- Düğümleri yeni düğümlerle değiştirerek tüm düğüm kümesini değiştirin. Bu, <xref:System.Xml.XmlNode.InnerXml%2A> özelliği kullanılarak yapılır.  
  
- <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemini kullanarak var olan düğümleri yeni düğümlerle değiştirin.  
  
- <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>veya <xref:System.Xml.XmlCharacterData.ReplaceData%2A> yöntemlerini kullanarak <xref:System.Xml.XmlCharacterData> sınıfından kalıtımla alan düğümlere ek karakterler ekleyin.  
  
- <xref:System.Xml.XmlCharacterData>öğesinden devraldığı düğüm türlerindeki <xref:System.Xml.XmlCharacterData.DeleteData%2A> yöntemi kullanarak bir karakter aralığını kaldırarak içeriği değiştirin.  
  
 Bir düğümün değerini değiştirmenin basit bir tekniği `node.Value = "new value";`kullanmaktır. Aşağıdaki tabloda bu tek kod satırının üzerinde çalışma ve bu düğüm türü için tam olarak hangi verilerin değiştiği düğüm türleri listelenmektedir.  
  
|Düğüm türü|Değiştirilen veriler|  
|---------------|------------------|  
|Öznitelik|Özniteliğin değeri.|  
|CDATASection|CDATASection içeriği.|  
|Yorum|Yorumun içeriği.|  
|Processingyönergesi|Hedef hariç içerik.|  
|Metin|Metnin içeriği.|  
|XmlDeclaration|`<?xml` ve `?>` işaretlemesi hariç, bildirimin içeriği.|  
|Boşlu|Boşluk değeri. Değeri, tanınan dört XML boşluk karakterinden biri olacak şekilde ayarlayabilirsiniz: boşluk, sekme, CR veya LF.|  
|SignificantWhitespace|Önemli boşluk değeri. Değeri, tanınan dört XML boşluk karakterinden biri olacak şekilde ayarlayabilirsiniz: boşluk, sekme, CR veya LF.|  
  
 Tabloda listelenmeyen hiçbir düğüm türü, üzerinde bir değer ayarlamak için geçerli bir düğüm türü değildir. Diğer herhangi bir düğüm türünde bir değer ayarlamak bir <xref:System.InvalidOperationException>oluşturur.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> özelliği, geçerli düğüm için alt düğümlerin işaretlemesini değiştirir. Bu özelliğin ayarlanması, alt düğümlerin belirtilen dizenin ayrıştırılmış içeriğiyle yerini alır. Ayrıştırma geçerli ad alanı bağlamında yapılır. Ayrıca, <xref:System.Xml.XmlNode.InnerXml%2A> gereksiz ad alanı bildirimlerini kaldırır. Sonuç olarak, çok sayıda kesme ve yapıştırma işlemi belgenizin boyutunu gereksiz ad alanı bildirimleriyle artırmaz. <xref:System.Xml.XmlNode.InnerXml%2A> işleminde ad alanlarının etkisini gösteren bir kod örneği için, <xref:System.Xml.XmlDocument.InnerXml%2A> özelliğine bakın.  
  
 <xref:System.Xml.XmlCharacterData.ReplaceData%2A> ve <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemleri kullanılırken, Yöntemler değiştirilmiş veya kaldırılmış düğümü döndürür. Daha sonra bu düğüm, XML Belge Nesne Modeli (DOM) içinde başka bir yere yeniden eklenebilir. <xref:System.Xml.XmlCharacterData.ReplaceData%2A> yöntemi, belgeye eklenmekte olan düğümde iki doğrulama denetimi yapar. İlk denetim, düğümün kendi türünün alt düğümlerine sahip olan bir düğümün alt öğesi haline gelmesini sağlar. İkinci denetim, eklenmekte olan düğümün alt öğesi olan düğümün üst öğesi olmamasını sağlar. Bu koşullardan birini ihlal eden bir <xref:System.InvalidOperationException>oluşturur.  
  
 Düzenlenebilecek bir düğümden salt okunurdur bir alt öğe eklemek veya kaldırmak için geçerlidir. Ancak, salt okunurdur bir düğümü değiştirme girişimleri bir <xref:System.InvalidOperationException>oluşturur. Bunun bir örneği, bir <xref:System.Xml.XmlEntityReference> düğümünün alt öğelerini değiştiriyor. Alt öğeler salt okunurdur ve değiştirilemez. Bunları değiştirme girişimleri bir <xref:System.InvalidOperationException>oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
