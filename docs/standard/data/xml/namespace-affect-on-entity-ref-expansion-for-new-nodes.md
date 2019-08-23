---
title: Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a92f1b08719c926e6384c220e3695de26dbb4fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967323"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
Bir varlık bildiriminin içeriği neredeyse her şey içerebildiğinden, içeriğin gibi `<!ENTITY aname "<elem>test</elem>">`bir öğe içerebildiği bir olasılık vardır.  
  
 XML ayrıştırıldığında, `&aname;` ayrıştırma zamanında değiştirme içeriğiyle genişletilmez. XML genişletmesi bitmedi çünkü öğe için ad alanının çözümlenmesi, düğüm belgeye yerleştirilene kadar gerçekleşemez. Bu saate kadar, kapsamda ne ad alanı olduğuna ilişkin bir bilgi yoktur. Düğüm belgeye eklendiğinde, ad alanı çözümlemesi oluşur ve sonuçta elde edilen varlık içeriği ilgili düğümlere ayrıştırılır.  
  
> [!NOTE]
> Yeni oluşturulan bir varlık başvurusu düğümünde genişletme gerçekleştikten sonra, hiçbir şekilde yeniden gerçekleşmez. Bu nedenle, öğe için değiştirme metninde kullanılan ad alanları, üst düğümün ayarlandığı zamanda bağlanır. Ancak, başka bir yerde veya **CloneNode** yöntemiyle kopyalanan varlık başvuru düğümlerinde bu ad alanı, var olan varlık başvuru düğümleri için değiştirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
