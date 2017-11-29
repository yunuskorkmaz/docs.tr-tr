---
title: "Nasıl yapılır: C# İçinde Sabitleri Tanımlama"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ff12d0b6882289da9ed924f1c7de00edc5dc1e2e
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
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
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
