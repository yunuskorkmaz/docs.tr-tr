---
title: "Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 029dffc878c62613e291620a2bd86971f369d15a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme #
Bazı durumlarda, bir uygulamada birden çok ayar kümesi sahip olmak isteyebilirsiniz. Belirli bir ayar grubu sık değiştirmek için beklenirken bir uygulama geliştiriyorsanız, örneğin, diğer ayarları etkilenmemesini değiştirmeden dosyası tümden değiştirilebilir böylece tüm tek bir dosyaya ayırmak akıllıca olabilir. Visual Studio projenize birden çok ayar kümesi eklemenizi sağlar. Ek ayarları kümesi Properties.Settings nesnesi erişilebilir.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Ek bir ayar kümesini uygulamanıza eklemek için  
  
1.  Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**. **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **ayarları dosyası**, dosya için bir ad yazın ve tıklayın **Ekle** çözümünüz için yeni bir ayarları dosyası eklemek için.  
  
3.  İçinde **Çözüm Gezgini**, yeni ayarları dosyasına sürükleyin **özellikleri** klasör. Bu yeni ayarlarınızı kodda kullanılabilir olmasını sağlar.  
  
4.  Ekleyin ve diğer ayarları dosyası gibi bu dosyada ayarları kullanın. Bu ayar grubu Properties.Settings nesnesi aracılığıyla erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
