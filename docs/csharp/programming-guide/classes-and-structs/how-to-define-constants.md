---
title: C# içinde sabitleri tanımlama
description: Değerlerini derleme zamanında ayarlanan alanlar olan C# ' de sabitleri nasıl tanımlayacağınızı öğrenin. Özel değerler için anlamlı adlar sağlamak üzere sabitleri kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: afa2799cf76f976e332f91b631dc90e2799a0aa0
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864650"
---
# <a name="how-to-define-constants-in-c"></a>C 'de sabitleri tanımlama\#
Sabitler, değerleri derleme zamanında ayarlanan alanlardır ve hiçbir zaman değiştirilemez. Özel değerler için sayısal değişmez değerler ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.  
  
> [!NOTE]
> C# ' de [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) Önişlemci yönergesi, sabitleri genellikle C ve C++ ' da kullanılan biçimde tanımlamak için kullanılamaz.  
  
 İntegral türlerinin sabit değerlerini ( `int` , `byte` , vb.) tanımlamak için numaralandırılmış bir tür kullanın. Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).  
  
 Tamsayı olmayan sabitleri tanımlamak için, tek bir yaklaşım bunları adlı tek bir statik sınıfta gruplamak olur `Constants` . Bu, aşağıdaki örnekte gösterildiği gibi sabitlerin tüm başvurularının sınıf adı ile önceden görüntülenmesini gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Sınıf adı niteleyicisi kullanımı, siz ve sabit kullanan diğer kişilerin sabit olduğunu ve değiştirilemeyeceğini anlamasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve yapılar](./index.md)
