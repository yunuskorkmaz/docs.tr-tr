---
title: Sabitlere Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 9ccddfe44757c76992d641094e21ec8c2110ef83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338348"
---
# <a name="constants-overview-visual-basic"></a>Sabitlere Genel Bakış (Visual Basic)
Sabit, değişmez bir sayının veya dizenin yerini alan anlamlı bir addır. Adın gösterdiği gibi sabitler depolama değerleri, uygulamanın yürütülmesi boyunca aynı kalır. Kodunuzun okunabilirliğini büyük ölçüde geliştirebilirsiniz ve sabitleri kullanarak daha kolay koruma sağlayabilirsiniz. Bunları yeniden görüntülenen veya belirgin bir anlamı olmayan belirli numaralara bağlı olan değerleri içeren kodda kullanın.  
  
## <a name="how-to-create-and-use-constants"></a>Sabitleri oluşturma ve kullanma  
 Visual Basic, genellikle yazdırma ve görüntüleme için kullanılan bir dizi önceden tanımlanmış sabitler içerir. Ayrıca, `Const` ifadesiyle kendi sabitlerinizi oluşturarak, bir değişken adı oluşturmak için kullandığınız yönergeleri kullanabilirsiniz. `Option Strict` `On`, sabit türü açıkça bildirmeniz gerekir.  
  
 Bir sabitin, adını nitelemeden kendisine başvurabilen tüm kod kümesi, aynı konumda bildirildiği değişkenle aynı. Belirli bir yordamın kapsamında var olan bir sabit oluşturmak için, bu yordamın içinde bildirin. Bir uygulamanın tamamında kullanılabilir bir sabit oluşturmak için, sınıfının bildirimler bölümündeki `Public` anahtar sözcüğünü kullanarak bildirin.  
  
> [!NOTE]
> Sabitler değişkenlere benzer olsa da, değişkenleri değiştiremeyeceğiniz sürece bunları değiştiremez veya yeni değerler atayamazsınız.  
  
 Kodunuzda kullandığınız sabitler, birlikte çalıştığınız denetimler veya bileşenler için nesne modeli tarafından tanımlanabilir veya Kullanıcı tanımlı (diğer bir deyişle, sizin oluşturduğunuz) olabilir.  
  
## <a name="compile-time-and-run-time-constants"></a>Derleme zamanı ve çalışma zamanı sabitleri  
 Derleme zamanı sabiti, kodun derlenmesi sırasında hesaplanır, ancak bir çalışma zamanı sabiti yalnızca uygulama çalışırken hesaplanabilir. Bir derleme zamanı sabiti her seferinde aynı değere sahip olacaktır, ancak bir çalışma zamanı sabiti her seferinde değişebilir. Dizi sınırları, Case ifadeleri veya Numaralandırıcı başlatıcıları gibi durumlar için derleme zamanı sabitleri gereklidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Tanım|Terim|  
|---|---|  
|[Nasıl yapılır: Bir Sabit Bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|`Const` deyimin bir sabiti bildirmek ve değerini ayarlamak için nasıl kullanılacağını açıklar; bir sabiti bildirerek değere anlamlı bir ad atarsınız.|  
|[Kullanıcı Tanımlı Sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Kapsam ve dairesel başvuruların nasıl engelleneceği hakkında bilgiler de dahil olmak üzere kendi sabitlerinizi oluşturmayı açıklar.|  
|[Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|`Option Explicit` kapalıyken Visual Basic derleyicisinin sabitleri nasıl Başlatan hakkında bilgi sağlar.|  
|[Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|İlgili sabit değerlerin nasıl gruplandırılacağını gösterir.|  
  
## <a name="reference"></a>Başvuru  
  
|Tanım|Terim|  
|---|---|  
|[Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Visual Basic tarafından önceden tanımlanan sabitleri listeler.|  
|[Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)|`Const` ifadesini ve kullanımını açıklar.|  
|[Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|`Option Strict` ifadesini ve kullanımını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Nasıl yapılır: Visual Basic dizi değişkenini başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
