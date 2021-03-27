---
title: C# içinde sabitleri tanımlama
description: Değerlerini derleme zamanında ayarlanan alanlar olan C# ' de sabitleri nasıl tanımlayacağınızı öğrenin. Özel değerler için anlamlı adlar sağlamak üzere sabitleri kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 54b8a335279c8bb81bc75d182ec653e434ab45a0
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636863"
---
# <a name="how-to-define-constants-in-c"></a>C 'de sabitleri tanımlama\#

Sabitler, değerleri derleme zamanında ayarlanan alanlardır ve hiçbir zaman değiştirilemez. Özel değerler için sayısal değişmez değerler ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.  
  
> [!NOTE]
> C# ' de [#define](../../language-reference/preprocessor-directives.md#defining-symbols) Önişlemci yönergesi, sabitleri genellikle C ve C++ ' da kullanılan biçimde tanımlamak için kullanılamaz.  
  
 İntegral türlerinin sabit değerlerini ( `int` , `byte` , vb.) tanımlamak için numaralandırılmış bir tür kullanın. Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).  
  
 Tamsayı olmayan sabitleri tanımlamak için, tek bir yaklaşım bunları adlı tek bir statik sınıfta gruplamak olur `Constants` . Bu, aşağıdaki örnekte gösterildiği gibi sabitlerin tüm başvurularının sınıf adı ile önceden görüntülenmesini gerektirir.  
  
## <a name="example"></a>Örnek  

 [!code-csharp[constants](snippets/how-to-define-constants/Program.cs)]  
  
 Sınıf adı niteleyicisi kullanımı, siz ve sabit kullanan diğer kişilerin sabit olduğunu ve değiştirilemeyeceğini anlamasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve Yapılar](./index.md)
