---
title: 'Nasıl yapılır: Uygulamanızda birden çok ayar kümesi eklemeC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 43402d8a1b0b1ca26e656be1424a5fa341ac4728
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719656"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Nasıl yapılır: C uygulamanızda birden çok ayar kümesi ekleme\#
Bazı durumlarda, bir uygulamada birden çok ayar kümesi olmasını isteyebilirsiniz. Burada belirli bir grubun ayarlarının sık değiştirilmesi beklenmeyen bir uygulama geliştiriyorsanız, örneğin, Etkilenmeyen diğer ayarları değiştirmeden böylece dosyayı tümden değiştirilebilir tümü tek bir dosyaya ayırarak akıllıca olabilir. Visual Studio projenize birden çok ayar kümesi eklemenizi sağlar. Ek ayarları kümesi Properties.Settings nesnesi erişilebilir.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Uygulamanıza ek bir ayar kümesi eklemek için  
  
1.  Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**. **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **ayarları dosyası**, dosya için bir ad yazın ve tıklayın **Ekle** çözümünüze yeni bir ayarlar dosyası eklemek için.  
  
3.  İçinde **Çözüm Gezgini**, yeni ayarları dosyasına sürükleyin **özellikleri** klasör. Bu yeni ayarlarınızı kodda kullanılabilir olmasını sağlar.  
  
4.  Ekleme ve diğer ayarları dosyası gibi bu dosyada ayarları kullanın. Bu Grup ayarlarını Properties.Settings nesnesi aracılığıyla erişebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
