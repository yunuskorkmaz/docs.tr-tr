---
title: "Sabitlere Genel Bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6526f7270602b3e1a4e8d953732c393ff252b2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-overview-visual-basic"></a>Sabitlere Genel Bakış (Visual Basic)
Bir sabit bir sayı veya değişmez dize yerini alır anlamlı bir addır. Adından da anlaşılacağı gibi bir uygulamanın yürütmesini boyunca aynı kalır değerleri sabitleri depolar. Büyük ölçüde kodunuzun okunabilirliğini artırmak ve sabitleri kullanarak bakımını kolaylaştırır. Yeniden değerleri içeren kodda kullanın veya hatırlamak veya belirgin bir anlama sahip zor olan belirli numaralarında bağlıdır.  
  
## <a name="how-to-create-and-use-constants"></a>Oluşturma ve kullanma sabitleri  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Yazdırma ve görüntüleme için temel olarak kullanarak, önceden tanımlanmış sabitleri sayısını içerir. Kendi değerlerinizi ile de oluşturabilirsiniz `Const` deyimi, bir değişken adı oluşturmak için yaptığınız aynı yönergeleri kullanarak. Varsa `Option Strict` olan `On`, açıkça sabit türü belirtmesi gerekir.  
  
 Adını niteleme olmadan başvurduğu tüm kod kümesidir, sabit 's kapsamı, aynı konumda bildirilen bir değişken aynıdır. Belirli bir yordamın kapsamında mevcut bir sabit oluşturmak için bu yordamı içinde bildirin. Bir uygulama genelinde kullanılabilir bir sabit oluşturmak için kullanarak bildirme `Public` sınıf bildirimleri bölümünde anahtar sözcüğü.  
  
> [!NOTE]
>  Sabitler biraz değişkenleri benzer ancak bunları değiştiremez veya değişkenleri yapabildiğiniz gibi yeni değerler atayabilirsiniz.  
  
 Kodunuzda kullandığınız sabitleri denetimleri veya ile çalışırsınız bileşenleri için nesne modeli tarafından tanımlanan veya kullanıcı tanımlı (diğer bir deyişle, bu sizin oluşturduğunuz).  
  
## <a name="compile-time-and-run-time-constants"></a>Derleme zamanı ve çalışma zamanı sabitleri  
 Derleme zamanı sabiti uygulama çalışırken, yalnızca bir çalışma zamanı sabit hesaplanabilir sırada kodu derlenmiş aynı anda hesaplanır. Derleme zamanı sabiti her zaman bir çalışma zamanı sabit değişebilir sırada bir uygulama, her çalıştığında aynı değere sahip. Derleme zamanı sabitleri dizi sınırları, case ifadeleri veya numaralandırıcı başlatıcıları gibi durumlarda gereklidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Tanım|Terim|  
|---|---|  
|[Nasıl yapılır: bir sabit bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Nasıl kullanılacağı açıklanmaktadır `Const` deyimi bir sabit bildirme ve; değeri ayarlamak için bir sabit bildirerek, anlamlı bir ad değeri atayın.|  
|[Kullanıcı tanımlı sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Kapsam hakkında bilgiler dahil olmak üzere kendi sabitler oluşturmak ve döngüsel başvurulara önlemek açıklar.|  
|[Sabit ve değişmez değerli veri türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Bilgi üzerinde nasıl sağlar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici başlatır sabitleri zaman `Option Explicit` kapalıdır.|  
|[Nasıl yapılır: ilgili sabit değerleri birlikte grubu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|İlgili sabit değerleri grubuna gösterilmiştir.|  
  
## <a name="reference"></a>Başvuru  
  
|Tanım|Terim|  
|---|---|  
|[Sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Tarafından önceden tanımlanmış sabitleri listeler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].|  
|[Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)|Açıklar `Const` deyimi ve kullanımı.|  
|[Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Açıklar `Option Strict` deyimi ve kullanımı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalara genel bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
