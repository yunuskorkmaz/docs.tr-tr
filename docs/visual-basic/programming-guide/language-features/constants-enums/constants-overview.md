---
title: Sabitlere Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2939110de77718baf32e2a0d8f1aa52dba997cf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907094"
---
# <a name="constants-overview-visual-basic"></a>Sabitlere Genel Bakış (Visual Basic)
Bir sayı veya dize değişmez yerini alır, anlamlı bir ad bir sabittir. Sabitler adından da anlaşılacağı gibi bir uygulamanın yürütülmesini boyunca değişmez değerlerini depolar. Büyük ölçüde kodunuzun okunabilirliği geliştirmek ve sabitleri kullanarak korumak üzere kolaylaştırır. Bunları yeniden değerleri içeren kodda kullanın veya, belirgin bir anlamı yoktur veya unutmayın zor olan belirli numaralarını bağlıdır.  
  
## <a name="how-to-create-and-use-constants"></a>Oluşturma ve sabitleri kullanın  
 Visual Basic, yazdırma ve görüntüleme için temel olarak kullanarak bir dizi önceden tanımlanmış sabitleri içerir. Ayrıca kendi sabitleriyle oluşturabilirsiniz `Const` deyimi, bir değişken adı oluşturmak için yaptığınız aynı yönergeleri kullanarak. Varsa `Option Strict` olduğu `On`, sabit türün açıkça belirtmesi gerekir.  
  
 Adıyla nitelemeden başvurduğu tüm kod kümesi olduğundan, bir sabitin kapsamı, aynı konumda bildirilen bir değişken, aynıdır. Belirli bir yordam kapsamında var olan bir sabit oluşturmak için bu yordam içinde bildirin. Bir uygulamanın tamamında kullanılabilir bir sabit değer oluşturmak için kullanarak bildirin `Public` sınıf bildirimleri bölümünde anahtar sözcüğü.  
  
> [!NOTE]
>  Sabitleri, değişkenleri biraz benzer olsa da, bunları değiştiremez veya değişkenleri için mümkün olduğunca yeni değerler atayabilirsiniz.  
  
 Kodunuzda kullandığınız sabitleri denetimleri veya bileşenleri ile çalışmak için nesne modeli tarafından tanımlanabilir veya kullanıcı tanımlı (diğer bir deyişle, bunlar sizin oluşturduğunuz).  
  
## <a name="compile-time-and-run-time-constants"></a>Derleme zamanı ve çalışma zamanı sabitleri  
 Uygulama çalışırken, yalnızca bir çalışma zamanı sabit hesaplanabilir sırasında kodu derlenmiş zamanında bir derleme zamanı sabiti hesaplanır. Bir derleme zamanı sabiti bir uygulamayı çalıştıran her zaman bir çalışma zamanı sabit değişebilir ancak her zaman aynı değere sahip. Derleme zamanı sabitleri dizi sınırları, case ifadesi veya numaralandırıcı başlatıcılar gibi durumlarda gereklidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Tanım|Terim|  
|---|---|  
|[Nasıl yapılır: Bir sabit bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Nasıl kullanılacağını açıklar `Const` ifadesi bir sabit bildirme ve; değeri ayarlamak için bir sabit bildirerek, anlamlı bir ad değer atayın.|  
|[Kullanıcı Tanımlı Sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Kapsamlar hakkında bilgiler dahil olmak üzere, kendi sabitleri oluşturma ve döngüsel başvuru kaçınmak nasıl açıklar.|  
|[Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Visual Basic derleyici sabitleri nasıl başlatır bilgiler sağlar, `Option Explicit` devre dışıdır.|  
|[Nasıl yapılır: İlgili sabit değerleri birlikte gruplandırma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|İlgili sabit değerleri nasıl gruplandırması gösterir.|  
  
## <a name="reference"></a>Başvuru  
  
|Tanım|Terim|  
|---|---|  
|[Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Visual Basic tarafından önceden tanımlanmış sabitleri listeler.|  
|[Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)|Açıklar `Const` deyimi ve kullanımı.|  
|[Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Açıklar `Option Strict` deyimi ve kullanımı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
