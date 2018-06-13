---
title: Sabitlere Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2ec43254013df5444048b5197489c55217d5328a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648391"
---
# <a name="constants-overview-visual-basic"></a>Sabitlere Genel Bakış (Visual Basic)
Bir sabit bir sayı veya değişmez dize yerini alır anlamlı bir addır. Adından da anlaşılacağı gibi bir uygulamanın yürütmesini boyunca aynı kalır değerleri sabitleri depolar. Büyük ölçüde kodunuzun okunabilirliğini artırmak ve sabitleri kullanarak bakımını kolaylaştırır. Yeniden değerleri içeren kodda kullanın veya hatırlamak veya belirgin bir anlama sahip zor olan belirli numaralarında bağlıdır.  
  
## <a name="how-to-create-and-use-constants"></a>Oluşturma ve kullanma sabitleri  
 Visual Basic, yazdırma ve görüntüleme için temel olarak kullanarak bir dizi önceden tanımlanmış sabitleri içerir. Kendi değerlerinizi ile de oluşturabilirsiniz `Const` deyimi, bir değişken adı oluşturmak için yaptığınız aynı yönergeleri kullanarak. Varsa `Option Strict` olan `On`, açıkça sabit türü belirtmesi gerekir.  
  
 Adını niteleme olmadan başvurduğu tüm kod kümesidir, sabit 's kapsamı, aynı konumda bildirilen bir değişken aynıdır. Belirli bir yordamın kapsamında mevcut bir sabit oluşturmak için bu yordamı içinde bildirin. Bir uygulama genelinde kullanılabilir bir sabit oluşturmak için kullanarak bildirme `Public` sınıf bildirimleri bölümünde anahtar sözcüğü.  
  
> [!NOTE]
>  Sabitler biraz değişkenleri benzer ancak bunları değiştiremez veya değişkenleri yapabildiğiniz gibi yeni değerler atayabilirsiniz.  
  
 Kodunuzda kullandığınız sabitleri denetimleri veya ile çalışırsınız bileşenleri için nesne modeli tarafından tanımlanan veya kullanıcı tanımlı (diğer bir deyişle, bu sizin oluşturduğunuz).  
  
## <a name="compile-time-and-run-time-constants"></a>Derleme zamanı ve çalışma zamanı sabitleri  
 Derleme zamanı sabiti uygulama çalışırken, yalnızca bir çalışma zamanı sabit hesaplanabilir sırada kodu derlenmiş aynı anda hesaplanır. Derleme zamanı sabiti her zaman bir çalışma zamanı sabit değişebilir sırada bir uygulama, her çalıştığında aynı değere sahip. Derleme zamanı sabitleri dizi sınırları, case ifadeleri veya numaralandırıcı başlatıcıları gibi durumlarda gereklidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Tanım|Terim|  
|---|---|  
|[Nasıl yapılır: Bir Sabit Bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Nasıl kullanılacağı açıklanmaktadır `Const` deyimi bir sabit bildirme ve; değeri ayarlamak için bir sabit bildirerek, anlamlı bir ad değeri atayın.|  
|[Kullanıcı Tanımlı Sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Kapsam hakkında bilgiler dahil olmak üzere kendi sabitler oluşturmak ve döngüsel başvurulara önlemek açıklar.|  
|[Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Visual Basic derleyici sabitleri nasıl başlatır bilgiler sağlar, `Option Explicit` kapalıdır.|  
|[Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|İlgili sabit değerleri grubuna gösterilmiştir.|  
  
## <a name="reference"></a>Başvuru  
  
|Tanım|Terim|  
|---|---|  
|[Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Visual Basic tarafından önceden tanımlanmış sabitleri listeler.|  
|[Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)|Açıklar `Const` deyimi ve kullanımı.|  
|[Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Açıklar `Option Strict` deyimi ve kullanımı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
