---
description: 'Daha fazla bilgi edinin: kodda öğe adları olarak anahtar sözcükler (Visual Basic)'
title: Code’da Öğe Adları Olarak Anahtar Sözcükler
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 4782c0f3ea065e3e140d449575c187cf2254cd08
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433219"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)

Değişken, sınıf veya üye gibi herhangi bir program öğesi, kısıtlanmış bir anahtar sözcükle aynı ada sahip olabilir. Örneğin, adlı bir değişken oluşturabilirsiniz `Loop` . Bununla birlikte, kısıtlanmış anahtar sözcüğüyle aynı ada sahip olan kendi sürümünüze başvurmak için, `Loop` `[ ]` Aşağıdaki örnekte gösterildiği gibi, tam nitelendirme dizesi ile önce veya köşeli ayraç () içine almanız gerekir.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Bunlardan herhangi birini yapmazsanız, Visual Basic iç `Loop` anahtar sözcüğünün kullanımını varsayar ve aşağıdaki örnekte olduğu gibi bir hata üretir:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Formlara ve denetimlere başvururken ve bir değişkeni bildirirken veya kısıtlanmış bir anahtar sözcükle aynı ada sahip bir yordam tanımlarken köşeli ayraçları kullanabilirsiniz. Adları nitelendirmek veya köşeli ayraçları dahil etmek kolay bir şekilde unutmak ve bu sayede kodunuzda hata ortaya çıkaracak ve okumayı zorlaştırmak kolaylaşır. Bu nedenle, program öğelerinin adları olarak kısıtlı anahtar sözcükleri kullanmanızı öneririz. Ancak, Visual Basic gelecek bir sürümü varolan bir formla veya denetim adıyla çakışan yeni bir anahtar sözcük tanımlıyorsa, kodunuzu yeni sürümle çalışacak şekilde güncelleştirirken bu tekniği kullanabilirsiniz.  
  
> [!NOTE]
> Programınız aynı zamanda başvurulan diğer derlemeler tarafından verilen öğe adlarını da içerebilir. Bu adlar, kısıtlanmış anahtar sözcüklerle çakışıyorsa, köşeli ayraç yerleştirmek Visual Basic, bunları tanımladığınız öğeler olarak yorumlamasına neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Adlandırma Kuralları](naming-conventions.md)
- [Program yapısı ve kod kuralları](program-structure-and-code-conventions.md)
- [Anahtar sözcükler](../../language-reference/keywords/index.md)
