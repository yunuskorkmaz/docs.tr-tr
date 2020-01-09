---
title: C# içinde sabitleri tanımlama
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337651"
---
# <a name="how-to-define-constants-in-c"></a>C\# sabitleri tanımlama
Sabitler, değerleri derleme zamanında ayarlanan alanlardır ve hiçbir zaman değiştirilemez. Özel değerler için sayısal değişmez değerler ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.  
  
> [!NOTE]
> C# [#Define](../../language-reference/preprocessor-directives/preprocessor-define.md) Önişlemci yönergesinde, sabitleri genellikle C ve C++içinde kullanılan biçimde tanımlamak için kullanılamaz.  
  
 İntegral türlerinin sabit değerlerini (`int`, `byte`vb.) tanımlamak için numaralandırılmış bir tür kullanın. Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).  
  
 Tamsayı olmayan sabitleri tanımlamak için, tek bir yaklaşım onları `Constants`adlı tek bir statik sınıfta gruplandırmaya yönelik bir yaklaşımdır. Bu, aşağıdaki örnekte gösterildiği gibi sabitlerin tüm başvurularının sınıf adı ile önceden görüntülenmesini gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Sınıf adı niteleyicisi kullanımı, siz ve sabit kullanan diğer kişilerin sabit olduğunu ve değiştirilemeyeceğini anlamasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve Yapılar](./index.md)
