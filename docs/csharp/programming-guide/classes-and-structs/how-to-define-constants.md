---
title: 'Nasıl yapılır: C# İçinde Sabitleri Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 03912a71aba883ec9127d265e6f1a2b05e1e60fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-constants-in-c"></a>Nasıl yapılır: C# İçinde Sabitleri Tanımlama
Sabit değerleri belirlenmiş alanları derleme zamanı ve hiçbir zaman değiştirilemez vardır. Sabitler sayısal değişmez değerleri ("Sihirli sayı") yerine anlamlı bir ad için özel değerler sağlamak için kullanın.  
  
> [!NOTE]
>  C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) önişlemci yönergesi, genellikle C ve C++ kullanılan şekilde sabitleri tanımlamak için kullanılamaz.  
  
 Tam sayı türleri sabit değerleri tanımlamak için (`int`, `byte`, vb.) bir numaralandırılmış türünü kullanın. Daha fazla bilgi için bkz: [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 İntegral olmayan sabitleri tanımlamak için adlı tek bir statik sınıf grup için bir yaklaşım ise `Constants`. Bu sınıf adıyla sabitlere yapılan tüm başvurular başında aşağıdaki örnekte gösterildiği gibi gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 Sınıf adı niteleyici kullanımını sizin ve başkalarının sabiti kullanan sabittir ve değiştirilemez anladığınızdan emin olun yardımcı olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
