---
title: ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406475"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.
ASP.NET içindeki katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez. XML özelliklerini kullanmak için kodu arka plan kodu ' na taşıyın.  
  
 Bir XML sabit değeri veya XML axis özelliği, bir ASP.NET dosyasında katıştırılmış kod () içinde tanımlanır `<%= =>` .  
  
 **Hata kimliği:** BC31200  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- XML literal veya XML Axis özelliğini içeren kodu bir ASP.NET arka plan kod dosyasına taşıyın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Değişmez Değerleri](../xml-literals/index.md)
- [XML Eksen Özellikleri](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
