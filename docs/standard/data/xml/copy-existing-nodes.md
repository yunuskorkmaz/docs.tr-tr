---
title: Var olan düğümleri kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252876"
---
# <a name="copy-existing-nodes"></a>Var olan düğümleri kopyalama
Birçok yöntem ve Özellikler içinde XML belge nesne modeli (gibi bir düğümü seçmek için kullanabileceğiniz DOM) vardır **SelectSingleNode**, **ChildNodes [int i]**, **öznitelikleri [int miyim]**. Düğüm seçildikten sonra bu belirli düğüm türü için çalışan INSERT yöntemlerden birini kullanarak ağaca ekleyebilirsiniz. Ağacına bir düğüm eklemek için tek bir kısıtlama düğüm ekledikten sonra belgeyi yine de iyi biçimlendirilmiş olması gerekliliğidir. Varolan bir düğümü DOM ağacına eklendiğinde, özgün konumundan kaldırıldı ve hedef konumuna eklendi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
