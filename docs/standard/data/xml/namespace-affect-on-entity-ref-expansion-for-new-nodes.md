---
description: 'Daha fazla bilgi: öğe ve öznitelik Içeren yeni düğümler için varlık başvurusu genişletmesi üzerinde ad alanı etkileri'
title: Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
ms.date: 03/30/2017
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 48345d75f9cf77f8e70655c8f166978cafbf06c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713487"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi

Bir varlık bildiriminin içeriği neredeyse her şey içerebildiğinden, içeriğin gibi bir öğe içerebildiği bir olasılık vardır `<!ENTITY aname "<elem>test</elem>">` .  
  
 XML ayrıştırıldığında, `&aname;` ayrıştırma zamanında değiştirme içeriğiyle genişletilmez. XML genişletmesi bitmedi çünkü öğe için ad alanının çözümlenmesi, düğüm belgeye yerleştirilene kadar gerçekleşemez. Bu saate kadar, kapsamda ne ad alanı olduğuna ilişkin bir bilgi yoktur. Düğüm belgeye eklendiğinde, ad alanı çözümlemesi oluşur ve sonuçta elde edilen varlık içeriği ilgili düğümlere ayrıştırılır.  
  
> [!NOTE]
> Yeni oluşturulan bir varlık başvurusu düğümünde genişletme gerçekleştikten sonra, hiçbir şekilde yeniden gerçekleşmez. Bu nedenle, öğe için değiştirme metninde kullanılan ad alanları, üst düğümün ayarlandığı zamanda bağlanır. Ancak, başka bir yerde veya **CloneNode** yöntemiyle kopyalanan varlık başvuru düğümlerinde bu ad alanı, var olan varlık başvuru düğümleri için değiştirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
