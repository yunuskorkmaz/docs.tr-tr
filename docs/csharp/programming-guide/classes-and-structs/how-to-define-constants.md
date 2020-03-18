---
title: C# içinde sabitleri tanımlama
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337651"
---
# <a name="how-to-define-constants-in-c"></a>C'de sabitler nasıl tanımlanır?\#
Sabitler, değerleri derleme zamanında ayarlanan ve asla değiştirilemeyecek alanlardır. Özel değerler için sayısal literaller ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.  
  
> [!NOTE]
> C# #define [önişlemci](../../language-reference/preprocessor-directives/preprocessor-define.md) yönergesi, sabitleri c ve c++'da genellikle kullanılan şekilde tanımlamak için kullanılamaz.  
  
 İntegral türlerinin`int`sabit `byte`değerlerini tanımlamak için (, , vb.) numaralandırılmış bir tür kullanın. Daha fazla bilgi için [enum' a](../../language-reference/builtin-types/enum.md)bakın.  
  
 İntegral olmayan sabitleri tanımlamak için bir yaklaşım, bunları `Constants`. Bu, aşağıdaki örnekte gösterildiği gibi, sabitlere yapılan tüm başvuruların sınıf adı ile ön karşıkarşıya olmasını gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Sınıf adı niteleyicisinin kullanımı, sizin ve sabiti kullanan diğer insanların bunun sabit olduğunu ve değiştirilemeyeceğini anlamanızı sağlamaya yardımcı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve Structs](./index.md)
