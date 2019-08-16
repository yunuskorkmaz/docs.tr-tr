---
title: "Nasıl yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040119"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Nasıl yapılır: C 'de uygulamanıza birden çok ayar kümesi ekleme\#

Bazı durumlarda, bir uygulamada birden fazla ayar kümesine sahip olmak isteyebilirsiniz. Örneğin, belirli bir ayar grubunun sıklıkla değiştirilmesi beklenen bir uygulama geliştiriyorsanız, dosyanın toplu olarak değiştirilebilmesi ve diğer ayarların etkilenmemesi için tümünü tek bir dosya halinde ayırmak sizin için gerekli olabilir. Visual Studio, projenize birden çok ayar kümesi eklemenize olanak tanır. `Properties.Settings` Nesne aracılığıyla ek ayar kümelerine erişilebilir.

## <a name="add-an-additional-set-of-settings"></a>Ek ayar kümesi ekleme

1. Visual Studio 'da, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

2. **Yeni öğe Ekle** iletişim kutusunda, **ayarlar dosyası**' nı seçin, dosya için bir ad girin ve çözümünüze yeni bir ayarlar dosyası eklemek için **Ekle** ' ye tıklayın.

3. **Çözüm Gezgini**, yeni ayarlar dosyasını **Özellikler** klasörüne sürükleyin. Bu, yeni ayarlarınızın kodda kullanılabilir olmasını sağlar.

4. Diğer ayarlar dosyası gibi bu dosyadaki ayarları ekleyin ve kullanın. Bu ayar grubuna `Properties.Settings` nesne aracılığıyla erişebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
