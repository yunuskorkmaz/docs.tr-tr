---
title: Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee45d983483d907b2a1e8b9e5ee12841e5c89c91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924117"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme
Düğümler ve belgedeki içeriği değiştirebilirsiniz birçok yolu vardır. Şunları yapabilirsiniz:  
  
- Kullanarak düğümlerin içerik modelini değiştirin <xref:System.Xml.XmlNode.Value%2A> özelliği.  
  
- Düğüm kümesinin tamamını, yeni düğümleri düğümler değiştirerek değiştirin. Bu yapılır kullanarak <xref:System.Xml.XmlNode.InnerXml%2A> özelliği.  
  
- Var olan düğümleri kullanarak yeni düğümler ile değiştirin <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemi.  
  
- Devralma düğümleri ek karakterleri eklemek <xref:System.Xml.XmlCharacterData> kullanarak <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, veya <xref:System.Xml.XmlCharacterData.ReplaceData%2A> yöntemleri.  
  
- Karakterleri kullanarak bir dizi kaldırarak içerik değiştirme <xref:System.Xml.XmlCharacterData.DeleteData%2A> yöntemi devralacak düğüm türleri üzerinde <xref:System.Xml.XmlCharacterData>.  
  
 Bir düğümün değerini değiştirmek için basit bir yöntem kullanmaktır `node.Value = "new value";`. Aşağıdaki tabloda, bu tek satırlık bir kod üzerinde çalıştığı düğüm türleri ve bu düğüm türü için hangi verilerin tam olarak değiştiğini listeler.  
  
|Düğüm türü|Değiştirilen veriler|  
|---------------|------------------|  
|Öznitelik|Öznitelik değeri.|  
|CDATASection|CDATASection içeriği.|  
|Yorum|İçerik açıklaması.|  
|İnstruction|Hedef hariç içeriği.|  
|Metin|Metin içeriği.|  
|XmlDeclaration|Bildirim içeriğini hariç `<?xml` ve `?>` biçimlendirme.|  
|Boşluk|Boşluk değeri. Dört tanınan XML boşluk karakterleri bir değere ayarlayabilirsiniz: boşluk, sekme, CR veya LF.|  
|SignificantWhitespace|Önemli boşluk değeri. Dört tanınan XML boşluk karakterleri bir değere ayarlayabilirsiniz: boşluk, sekme, CR veya LF.|  
  
 Tabloda listelenmeyen bir düğüm türü herhangi bir değeri ayarlamak için geçerli düğüm türü değil. Başka bir düğüm türü herhangi bir değere ayarlamak oluşturur bir <xref:System.InvalidOperationException>.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> Özelliğini geçerli düğümünün alt düğümleri biçimlerini değiştirir. Bu özelliğin ayarlanması alt düğümleri ayrıştırılmış içeriğini verilen dize ile değiştirir. Ayrıştırma geçerli bir ad alanı bağlamında gerçekleştirilir. Ayrıca, <xref:System.Xml.XmlNode.InnerXml%2A> yedekli ad alanı bildirimi kaldırır. Sonuç, çok sayıda kesme ve yapıştırma işlemlerini belgeniz ile yedekli ad alanı bildirimi boyutunu artırmaz gibi. Ad alanları etkisini gösteren bir kod örneği için <xref:System.Xml.XmlNode.InnerXml%2A> işlemi görmek <xref:System.Xml.XmlDocument.InnerXml%2A> özelliği.  
  
 Kullanırken <xref:System.Xml.XmlCharacterData.ReplaceData%2A> ve <xref:System.Xml.XmlNode.RemoveChild%2A> yöntemleri, yöntemleri, değiştirilen veya kaldırılan düğüm döndürür. Bu düğüm ardından yere başka XML belge nesne modeli (DOM) yeniden. <xref:System.Xml.XmlCharacterData.ReplaceData%2A> Yöntemi belgeye eklenen düğüm üzerinde iki doğrulama denetimleri yapar. İlk onay düğümünün alt düğümleri türüne sahip olabilecek bir düğümün alt düğümü gelmektedir sağlar. İkinci onay eklenen düğüm alt gelmektedir düğümünün üst öğesi değil sağlar. Bunlardan biri ihlal koşulları oluşturur bir <xref:System.InvalidOperationException>.  
  
 Eklemek veya salt okunur bir alt düzenlenebilir bir düğümden kaldırmak için geçerlidir. Ancak, salt okunur düğümü değiştirmeye çalıştığında oluşturur bir <xref:System.InvalidOperationException>. Buna örnek olarak, alt değiştirerek bir <xref:System.Xml.XmlEntityReference> düğümü. Alt salt okunurdur ve değiştirilemez. Yapmaya oluşturur değiştirilecek bir <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
