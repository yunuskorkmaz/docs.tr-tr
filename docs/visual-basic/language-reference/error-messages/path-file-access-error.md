---
title: Yol-dosya erişim hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 53f021faa9e4ae69a71d825ca823e1180421afc6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522485"
---
# <a name="pathfile-access-error"></a>Yol/Dosya erişim hatası
Bir dosya erişim veya disk erişimi işlemi sırasında işletim sistemi yolu ve dosya adı arasında bir bağlantı yapamadı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dosya belirtimi doğru biçimlendirildiğinden emin olun. Bir dosya adı bir tam (tam) veya göreli içerebilir yolu. (Yol, başka bir sürücüdeyse) tam yolu sürücü adıyla başlar ve kök dosyasının açık yolu listeler. Tam olmayan herhangi geçerli bir sürücü ve dizini göreli yoludur.  
  
2.  Varolan bir salt okunur dosyanın yerini alır bir dosyayı kaydetmeye denemedi emin olun. Bu durumda, hedef dosyanın salt okunur özniteliği değiştirin veya dosyayı farklı bir dosya adıyla kaydedin.  
  
3.  Siz deneme salt okunur bir dosya içinde sıralı açmak emin `Output` veya `Append` modu. Bu durumda, dosyayı açma `Input` modu veya değişiklik dosyanın salt okunur özniteliği.  
  
4.  Bir veritabanı ya da belge içinde bir Visual Basic projesi değiştirmek denemedi emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
