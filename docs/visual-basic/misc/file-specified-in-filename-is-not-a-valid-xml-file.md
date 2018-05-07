---
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 3aecb0c2c87539717656a29f5b48f94fce3c8453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Dosya adında belirtilen dosya geçerli bir XML dosyası değil
Sağladığınız dosya adı geçerli bir XML dosyası değil. XML belgesinin içeriğini ve izin verilen yapısı belirtmek için bir belge türü tanımı (DTD), bir Microsoft XML verileri azaltılmış (XDR) şema veya bir XML Şeması Tanım Dili (XSD) şeması kullanabilirsiniz. XSD şemaları olan XML aynı belirtmek için tercih edilen yol [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  Bazı sürümlerinde Visual Studio **XML Designer** yazılan veri kümeleri ve XML şema Tasarımcısı olur. **XML Designer** hala XML şema dosyalarını oluşturmak ve düzenlemek için kullanılabilir. Bununla birlikte, [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], oluşturma ve düzenleme yazılan veri kümeleri için tasarımcı **veri kümesi Tasarımcısı**. Daha fazla bilgi için bkz: [oluşturma ve düzenleme yazılan veri kümeleri](/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Doğru dosya adını sağladığını denetleyin.  
  
-   İçine denetlemek istediğiniz XML dosyası yüklenirken tarafından belirtilen dosya geçerli XML içerdiğini denetleyin **XML Designer**. Gelen **XML** menüsünde tıklatın **doğrulamak XML**. Hataları görüntülenir **görev listesi**.  
  
-   XML dosyası ilişkili bir XML şeması varsa, öğeleri tanımlanmış bir yapı içinde görünür ve ayrı ayrı öğeler içeriğini şemasında belirtilen bildirilen veri türleri için uygun denetleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml>  
 [Nasıl Yapılır: Dosya Yollarını Ayrıştırma](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
