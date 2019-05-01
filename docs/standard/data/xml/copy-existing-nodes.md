---
title: Var Olan Düğümleri Kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864136"
---
# <a name="copy-existing-nodes"></a>Var Olan Düğümleri Kopyalama
Birçok yöntem ve Özellikler içinde XML belge nesne modeli (gibi bir düğümü seçmek için kullanabileceğiniz DOM) vardır **SelectSingleNode**, **ChildNodes [int i]**, **öznitelikleri [int miyim]**. Düğüm seçildikten sonra bu belirli düğüm türü için çalışan INSERT yöntemlerden birini kullanarak ağaca ekleyebilirsiniz. Ağacına bir düğüm eklemek için tek bir kısıtlama düğüm ekledikten sonra belgeyi yine de iyi biçimlendirilmiş olması gerekliliğidir. Varolan bir düğümü DOM ağacına eklendiğinde, özgün konumundan kaldırıldı ve hedef konumuna eklendi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
