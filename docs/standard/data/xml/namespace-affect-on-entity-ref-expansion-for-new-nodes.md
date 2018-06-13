---
title: Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2ba9964f17380e868ea5fe906a40f8b491018a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568907"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme
Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden içeriği gibi bir öğe içerebilir olasılığı yok `<!ENTITY aname "<elem>test</elem>">`.  
  
 XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmiş değil. Düğümün belgede yerleştirilen kadar öğe için bir ad çözümlemesini gerçekleşemez çünkü XML genişletme yapılmadı. O zamana kadar hangi ad alanı kapsamında olup hiçbir bilgisi yoktur. Düğüm belgeye geçirdiğinizde, ad çözümlemesi oluşur ve içerik sonuç varlık uygun düğümlerinden ayrıştırılır.  
  
> [!NOTE]
>  Yeni oluşturulan varlık başvurusu düğümde genişletme oluşur sonra hiçbir zaman oluşana. Bu nedenle, öğe için değiştirme metinde kullanılan ad alanları üst düğüm kümesi aynı anda bağlanır. Ad alanı kaldırdığınızda ve başka bir yere yerleştirin varolan varlık başvurusu düğümleri için veya ile kopyalanması varlık başvurusu düğümlerde ancak değiştirilebilir **CloneNode** yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
