---
title: Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 05ec622f09106978281cd3e6f0a82f13703c2097
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288816"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
Bir varlık bildiriminin içeriği neredeyse her şey içerebildiğinden, içeriğin gibi bir öğe içerebildiği bir olasılık vardır `<!ENTITY aname "<elem>test</elem>">` .  
  
 XML ayrıştırıldığında, `&aname;` ayrıştırma zamanında değiştirme içeriğiyle genişletilmez. XML genişletmesi bitmedi çünkü öğe için ad alanının çözümlenmesi, düğüm belgeye yerleştirilene kadar gerçekleşemez. Bu saate kadar, kapsamda ne ad alanı olduğuna ilişkin bir bilgi yoktur. Düğüm belgeye eklendiğinde, ad alanı çözümlemesi oluşur ve sonuçta elde edilen varlık içeriği ilgili düğümlere ayrıştırılır.  
  
> [!NOTE]
> Yeni oluşturulan bir varlık başvurusu düğümünde genişletme gerçekleştikten sonra, hiçbir şekilde yeniden gerçekleşmez. Bu nedenle, öğe için değiştirme metninde kullanılan ad alanları, üst düğümün ayarlandığı zamanda bağlanır. Ancak, başka bir yerde veya **CloneNode** yöntemiyle kopyalanan varlık başvuru düğümlerinde bu ad alanı, var olan varlık başvuru düğümleri için değiştirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
