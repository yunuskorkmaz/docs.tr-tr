---
title: "Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme"
description: Visual Studio 'Yu kullanarak C# ' de uygulamanıza birden çok Windows Forms ayarları kümesi eklemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173451"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Nasıl yapılır: C 'de uygulamanıza birden çok ayar kümesi ekleme\#

Bazı durumlarda, bir uygulamada birden fazla ayar kümesine sahip olmak isteyebilirsiniz. Örneğin, belirli bir ayar grubunun sıklıkla değiştirilmesi beklenen bir uygulama geliştiriyorsanız, dosyanın toplu olarak değiştirilebilmesi ve diğer ayarların etkilenmemesi için tümünü tek bir dosya halinde ayırmak sizin için gerekli olabilir. Visual Studio, projenize birden çok ayar kümesi eklemenize olanak tanır. Nesne aracılığıyla ek ayar kümelerine erişilebilir `Properties.Settings` .

## <a name="add-an-additional-set-of-settings"></a>Ek ayar kümesi ekleme

1. Visual Studio 'da, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

2. **Yeni öğe Ekle** iletişim kutusunda, **ayarlar dosyası**' nı seçin, dosya için bir ad girin ve çözümünüze yeni bir ayarlar dosyası eklemek için **Ekle** ' ye tıklayın.

3. **Çözüm Gezgini**, yeni ayarlar dosyasını **Özellikler** klasörüne sürükleyin. Bu, yeni ayarlarınızın kodda kullanılabilir olmasını sağlar.

4. Diğer ayarlar dosyası gibi bu dosyadaki ayarları ekleyin ve kullanın. Bu ayar grubuna nesne aracılığıyla erişebilirsiniz `Properties.Settings` .

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
