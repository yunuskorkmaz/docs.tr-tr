---
description: 'Hakkında daha fazla bilgi edinin: BC31200: XML sabit değerleri ve XML özellikleri ASP.NET içindeki gömülü kodda desteklenmez'
title: ASP.NET içine katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez.
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 0a5328676ee38a56334b77f665a464daa586ce3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701410"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>BC31200: ASP.NET içindeki gömülü kodda XML sabit değerleri ve XML özellikleri desteklenmez

ASP.NET içindeki katıştırılmış kodda XML sabit değerleri ve XML özellikleri desteklenmez. XML özelliklerini kullanmak için kodu arka plan kodu ' na taşıyın.

 Bir XML sabit değeri veya XML axis özelliği, bir ASP.NET dosyasında katıştırılmış kod () içinde tanımlanır `<%= =>` .

 **Hata kimliği:** BC31200

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- XML literal veya XML Axis özelliğini içeren kodu bir ASP.NET arka plan kod dosyasına taşıyın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Değişmez Değerleri](../xml-literals/index.md)
- [XML Eksen Özellikleri](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
