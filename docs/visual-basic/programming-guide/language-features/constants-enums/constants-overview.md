---
title: Sabitlere Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 0c866f3d03d26bd882d5a6596d40d1dc639da011
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934777"
---
# <a name="constants-overview-visual-basic"></a>Sabitlere Genel Bakış (Visual Basic)
Sabit, değişmez bir sayının veya dizenin yerini alan anlamlı bir addır. Adın gösterdiği gibi sabitler depolama değerleri, uygulamanın yürütülmesi boyunca aynı kalır. Kodunuzun okunabilirliğini büyük ölçüde geliştirebilirsiniz ve sabitleri kullanarak daha kolay koruma sağlayabilirsiniz. Bunları yeniden görüntülenen veya belirgin bir anlamı olmayan belirli numaralara bağlı olan değerleri içeren kodda kullanın.  
  
## <a name="how-to-create-and-use-constants"></a>Sabitleri oluşturma ve kullanma  
 Visual Basic, genellikle yazdırma ve görüntüleme için kullanılan bir dizi önceden tanımlanmış sabitler içerir. Ayrıca, bir değişken adı oluşturmak için kullandığınız yönergeleri `Const` kullanarak deyimle kendi sabitlerinizi de oluşturabilirsiniz. `Option Strict` İse`On`, sabit türü açıkça bildirmeniz gerekir.  
  
 Bir sabitin, adını nitelemeden kendisine başvurabilen tüm kod kümesi, aynı konumda bildirildiği değişkenle aynı. Belirli bir yordamın kapsamında var olan bir sabit oluşturmak için, bu yordamın içinde bildirin. Bir uygulamanın tamamında kullanılabilir bir sabit oluşturmak için, sınıfının bildirimler bölümündeki `Public` anahtar sözcüğünü kullanarak bunu bildirin.  
  
> [!NOTE]
> Sabitler değişkenlere benzer olsa da, değişkenleri değiştiremeyeceğiniz sürece bunları değiştiremez veya yeni değerler atayamazsınız.  
  
 Kodunuzda kullandığınız sabitler, birlikte çalıştığınız denetimler veya bileşenler için nesne modeli tarafından tanımlanabilir veya Kullanıcı tanımlı (diğer bir deyişle, sizin oluşturduğunuz) olabilir.  
  
## <a name="compile-time-and-run-time-constants"></a>Derleme zamanı ve çalışma zamanı sabitleri  
 Derleme zamanı sabiti, kodun derlenmesi sırasında hesaplanır, ancak bir çalışma zamanı sabiti yalnızca uygulama çalışırken hesaplanabilir. Bir derleme zamanı sabiti her seferinde aynı değere sahip olacaktır, ancak bir çalışma zamanı sabiti her seferinde değişebilir. Dizi sınırları, Case ifadeleri veya Numaralandırıcı başlatıcıları gibi durumlar için derleme zamanı sabitleri gereklidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Tanım|Terim|  
|---|---|  
|[Nasıl yapılır: Sabit bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Bir sabiti bildirmek ve değerini `Const` ayarlamak için ifadesinin nasıl kullanılacağını açıklar; bir sabiti bildirerek değere anlamlı bir ad atarsınız.|  
|[Kullanıcı Tanımlı Sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Kapsam ve dairesel başvuruların nasıl engelleneceği hakkında bilgiler de dahil olmak üzere kendi sabitlerinizi oluşturmayı açıklar.|  
|[Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Kapatıldığında Visual Basic derleyicisinin sabitleri `Option Explicit` nasıl Başlatan hakkında bilgi sağlar.|  
|[Nasıl yapılır: Ilgili sabit değerleri birlikte grupla](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|İlgili sabit değerlerin nasıl gruplandırılacağını gösterir.|  
  
## <a name="reference"></a>Başvuru  
  
|Tanım|Terim|  
|---|---|  
|[Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Visual Basic tarafından önceden tanımlanan sabitleri listeler.|  
|[Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)|`Const` İfadesini ve kullanımını açıklar.|  
|[Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|`Option Strict` İfadesini ve kullanımını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Nasıl yapılır: Visual Basic bir dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
