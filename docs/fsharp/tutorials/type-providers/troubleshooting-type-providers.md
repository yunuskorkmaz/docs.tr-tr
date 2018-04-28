---
title: Tür Sağlayıcıları Sorunlarını Giderme
description: "Tür sağlayıcıları F #'de kullanırken karşılaşabileceğiniz en olası sorunlar için olası çözümleri keşfedin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e7374a051ca63e003288702c6d882e72d77d71e8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshooting-type-providers"></a>Tür Sağlayıcıları Sorunlarını Giderme

Bu konu açıklar ve tür sağlayıcıları kullandığınızda karşılaşabileceğiniz en olası sorunlar için olası çözümleri sağlar.


## <a name="possible-problems-with-type-providers"></a>Tür sağlayıcıları ile olası sorunlar
Tür sağlayıcıları ile çalışırken bir sorunla karşılaşırsanız, en yaygın çözümleri için aşağıdaki tabloyu gözden geçirebilirsiniz.



|Sorun|Önerilen Eylemler|
|-------|-----------------|
|**Şema değişiklikleri**. Veri kaynağı şeması kararlı olduğunda sağlayıcıları iş en iyi şekilde yazın. Veri tablosu veya sütun eklemek veya bu şemaya başka bir değişiklik, tür sağlayıcısı otomatik olarak bu değişiklikleri tanımaz.|Temiz veya projeyi yeniden oluşturun. Projeyi temizleyin tercih **yapı**, **temiz** *ProjectName* menü çubuğunda. Projeyi oluşturmak için tercih **yapı**, **yeniden** *ProjectName* menü çubuğunda. Bu eylemler tüm türü sağlayıcısı durumu sıfırlar ve veri kaynağına bağlanın ve güncelleştirilmiş şema bilgileri edinmek için sağlayıcı zorlar.|
|**Bağlantı hatası**. URL veya bağlantı dizesi hatalı, ağ bağlantısı kesilse veya veri kaynağı veya hizmet kullanılamıyor.|Web hizmeti veya OData hizmeti için Internet Explorer'ı URL'nin doğru olduğundan ve hizmeti kullanılabilir durumda olup olmadığını doğrulamak için URL'de deneyebilirsiniz. Bir veritabanı bağlantı dizesi için veri bağlantısı araçları kullanabilirsiniz **Sunucu Gezgini** bağlantı dizesi geçerli olduğundan ve veritabanının kullanılabilir durumda olup olmadığını doğrulayın. Bağlantınızı geri yükledikten sonra ardından temizlemek veya tür sağlayıcısı ağa yeniden böylece projeyi yeniden gerekir.|
|**Geçersiz kimlik bilgileri**. Veri kaynağı veya web hizmeti için geçerli izinlerine sahip olmalıdır.|SQL bağlantısı için kullanıcı adı ve bağlantı dizesi veya yapılandırma dosyasında belirtilen parola veritabanı için geçerli olmalıdır. Windows kimlik doğrulaması kullanıyorsanız, veritabanına erişim izni olmalıdır. Veritabanı yöneticisi izinleri için gereksinim duyduğunuz her veritabanı ve bir veritabanı içinde her öğe için erişim tanımlayabilirsiniz.<br /><br />Bir web hizmeti veya bir veri hizmeti için uygun kimlik bilgilerine sahip olması gerekir. Çoğu tür sağlayıcıları uygun kullanıcı adı ve erişim anahtarı ile ayarlayabileceğiniz bir kimlik özelliği içeren bir DataContext nesnesi sağlayın.|
|**Geçersiz yol**. Bir dosya yolu geçerli değil.|Yolun doğru olduğundan ve dosyanın var olup olmadığını doğrulayın. Ayrıca, tüm backlashes yolunda uygun şekilde teklif veya bir verbatim veya Üçlü tırnak içine alınmış dize kullanın.|

## <a name="see-also"></a>Ayrıca Bkz.
[Tür Sağlayıcıları](index.md)
