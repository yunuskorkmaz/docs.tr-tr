---
title: 'Nasıl yapılır: C# İçinde Sabitleri Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: a85e7728512922be38658c07314229c26b2461fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646455"
---
# <a name="how-to-define-constants-in-c"></a>Nasıl yapılır: C sabitleri tanımlama\#
Alanlar, değerleri kümesine derleme zamanı ve hiçbir zaman değiştirilebilir sabittir. Özel değerler için sayısal değişmez değerleri ("Sihirli sayı") yerine anlamlı adlar sağlamak için sabitleri kullanın.  
  
> [!NOTE]
>  C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) önişlemci yönergesi, genellikle C ve C++ içinde kullanılan bir şekilde sabitleri tanımlamak için kullanılamaz.  
  
 İntegral türündeki sabit değerler tanımlamak için (`int`, `byte`, vb.) bir listeden seçimli türü kullanın. Daha fazla bilgi için [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Tamsayı olmayan sabitleri tanımlamak için adlı tek bir statik sınıf içinde gruplamak için bir yaklaşım ise `Constants`. Bu sınıfı adıyla sabitlere yapılan tüm başvurular başında, aşağıdaki örnekte gösterildiği gibi gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Sınıf adı niteleyici kullanımını yardımcı olur ve sabit diğer sabittir ve değiştirilemez anladığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
