---
title: Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
ms.openlocfilehash: f544b7d8472285095af9a71b1c24f94f61f93bc6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288829"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme
Belgedeki düğümleri ve içerikleri değiştirebileceğiniz birçok yol vardır. Seçenekleriniz şunlardır:  
  
- Özelliğini kullanarak düğümlerin değerini değiştirin <xref:System.Xml.XmlNode.Value%2A> .  
  
- Düğümleri yeni düğümlerle değiştirerek tüm düğüm kümesini değiştirin. Bu, özelliği kullanılarak yapılır <xref:System.Xml.XmlNode.InnerXml%2A> .  
  
- Yöntemini kullanarak var olan düğümleri yeni düğümlerle değiştirin <xref:System.Xml.XmlNode.RemoveChild%2A> .  
  
- <xref:System.Xml.XmlCharacterData> <xref:System.Xml.XmlCharacterData.AppendData%2A> , <xref:System.Xml.XmlCharacterData.InsertData%2A> , Veya yöntemlerini kullanarak sınıftan devraldığı düğümlere ek karakterler ekleyin <xref:System.Xml.XmlCharacterData.ReplaceData%2A> .  
  
- <xref:System.Xml.XmlCharacterData.DeleteData%2A>Öğesinden devraldığı düğüm türlerindeki yöntemi kullanarak bir karakter aralığını kaldırarak içeriği değiştirin <xref:System.Xml.XmlCharacterData> .  
  
 Bir düğümün değerini değiştirmenin basit bir tekniği kullanmaktır `node.Value = "new value";` . Aşağıdaki tabloda bu tek kod satırının üzerinde çalışma ve bu düğüm türü için tam olarak hangi verilerin değiştiği düğüm türleri listelenmektedir.  
  
|Düğüm türü|Değiştirilen veriler|  
|---------------|------------------|  
|Öznitelik|Özniteliğin değeri.|  
|CDATASection|CDATASection içeriği.|  
|Yorum|Yorumun içeriği.|  
|Processingyönergesi|Hedef hariç içerik.|  
|Metin|Metnin içeriği.|  
|XmlDeclaration|Bildirim içeriği `<?xml` ve `?>` işaretleme hariç.|  
|Boşluk|Boşluk değeri. Değeri, tanınan dört XML boşluk karakterinden biri olacak şekilde ayarlayabilirsiniz: boşluk, sekme, CR veya LF.|  
|SignificantWhitespace|Önemli boşluk değeri. Değeri, tanınan dört XML boşluk karakterinden biri olacak şekilde ayarlayabilirsiniz: boşluk, sekme, CR veya LF.|  
  
 Tabloda listelenmeyen hiçbir düğüm türü, üzerinde bir değer ayarlamak için geçerli bir düğüm türü değildir. Diğer herhangi bir düğüm türünde bir değer ayarlamak bir oluşturur <xref:System.InvalidOperationException> .  
  
 <xref:System.Xml.XmlNode.InnerXml%2A>Özelliği, geçerli düğüm için alt düğümlerin işaretlemesini değiştirir. Bu özelliğin ayarlanması, alt düğümlerin belirtilen dizenin ayrıştırılmış içeriğiyle yerini alır. Ayrıştırma geçerli ad alanı bağlamında yapılır. Ayrıca, <xref:System.Xml.XmlNode.InnerXml%2A> gereksiz ad alanı bildirimlerini kaldırır. Sonuç olarak, çok sayıda kesme ve yapıştırma işlemi belgenizin boyutunu gereksiz ad alanı bildirimleriyle artırmaz. İşlemdeki ad alanlarının etkisini gösteren bir kod örneği için <xref:System.Xml.XmlNode.InnerXml%2A> bkz <xref:System.Xml.XmlDocument.InnerXml%2A> . özelliği.  
  
 <xref:System.Xml.XmlCharacterData.ReplaceData%2A>Ve <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemlerini kullanırken, Yöntemler değiştirilmiş veya kaldırılmış düğümü döndürür. Daha sonra bu düğüm, XML Belge Nesne Modeli (DOM) içinde başka bir yere yeniden eklenebilir. <xref:System.Xml.XmlCharacterData.ReplaceData%2A>Yöntemi, belgeye eklenmekte olan düğümde iki doğrulama denetimi yapar. İlk denetim, düğümün kendi türünün alt düğümlerine sahip olan bir düğümün alt öğesi haline gelmesini sağlar. İkinci denetim, eklenmekte olan düğümün alt öğesi olan düğümün üst öğesi olmamasını sağlar. Bu koşullardan birini ihlal eden bir <xref:System.InvalidOperationException> .  
  
 Düzenlenebilecek bir düğümden salt okunurdur bir alt öğe eklemek veya kaldırmak için geçerlidir. Ancak, salt okunurdur bir düğümü değiştirme girişimleri bir oluşturur <xref:System.InvalidOperationException> . Bunun bir örneği, bir düğümün alt öğelerini değiştiriyor <xref:System.Xml.XmlEntityReference> . Alt öğeler salt okunurdur ve değiştirilemez. Bunları değiştirme girişimleri bir oluşturur <xref:System.InvalidOperationException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
