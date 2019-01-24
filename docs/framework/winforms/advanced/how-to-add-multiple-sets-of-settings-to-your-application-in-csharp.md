---
title: 'Nasıl yapılır: Uygulamanızda birden çok ayar kümesi eklemeC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 5496d370890e019ae2b31835c95a9988f8d9bc18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559417"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Nasıl yapılır: Uygulamanızda birden çok ayar kümesi eklemeC# #
Bazı durumlarda, bir uygulamada birden çok ayar kümesi olmasını isteyebilirsiniz. Burada belirli bir grubun ayarlarının sık değiştirilmesi beklenmeyen bir uygulama geliştiriyorsanız, örneğin, Etkilenmeyen diğer ayarları değiştirmeden böylece dosyayı tümden değiştirilebilir tümü tek bir dosyaya ayırarak akıllıca olabilir. Visual Studio projenize birden çok ayar kümesi eklemenizi sağlar. Ek ayarları kümesi Properties.Settings nesnesi erişilebilir.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Uygulamanıza ek bir ayar kümesi eklemek için  
  
1.  Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**. **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **ayarları dosyası**, dosya için bir ad yazın ve tıklayın **Ekle** çözümünüze yeni bir ayarlar dosyası eklemek için.  
  
3.  İçinde **Çözüm Gezgini**, yeni ayarları dosyasına sürükleyin **özellikleri** klasör. Bu yeni ayarlarınızı kodda kullanılabilir olmasını sağlar.  
  
4.  Ekleme ve diğer ayarları dosyası gibi bu dosyada ayarları kullanın. Bu Grup ayarlarını Properties.Settings nesnesi aracılığıyla erişebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
