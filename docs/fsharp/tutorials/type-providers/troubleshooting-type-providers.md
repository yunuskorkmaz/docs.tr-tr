---
title: Tür Sağlayıcıları Sorunlarını Giderme
description: 'Tür sağlayıcıları F # kullanırken karşılaşabileceğiniz en olası sorunlar için olası çözümleri keşfedin.'
ms.date: 05/16/2016
ms.openlocfilehash: f3b8ffdaf615563305b7b84b45a9ed1e066d0dcc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685692"
---
# <a name="troubleshooting-type-providers"></a>Tür Sağlayıcıları Sorunlarını Giderme

Bu konu açıklar ve tür sağlayıcıları kullanırken karşılaşabileceğiniz en olası sorunlar için olası çözümleri sağlar.

## <a name="possible-problems-with-type-providers"></a>Tür sağlayıcıları ile olası sorunlar

Tür sağlayıcıları ile çalışırken bir sorunla karşılaşırsanız, en yaygın çözümleri için aşağıdaki tabloyu gözden geçirebilirsiniz.

|Sorun|Önerilen Eylemler|
|-------|-----------------|
|**Şema değişiklikleri**. Veri kaynağı şemasını kararlı olduğunda sağlayıcıları iş en iyi şekilde yazın. Veri tablosu veya sütun ekleme veya bu şema için başka bir değişiklik, tür sağlayıcısı bu değişiklikleri otomatik olarak tanımaz.|Temizlemek veya projeyi yeniden derleyin. Projeyi temizleyin, tercih **derleme**, **temiz** *ProjectName* menü çubuğundaki. Projeyi yeniden derlemek için seçin **derleme**, **yeniden** *ProjectName* menü çubuğundaki. Bu Eylemler, tüm tür sağlayıcısı durumunu sıfırlayın ve veri kaynağına bağlanın ve güncelleştirilmiş şema bilgileri edinmek için sağlayıcıyı zorlar.|
|**Bağlantı hatası**. URL veya bağlantı dizesi yanlış, ağ bağlantısı kesilse veya veri kaynağı veya hizmeti kullanılamıyor.|Bir web hizmeti veya OData hizmeti için Internet Explorer'ı URL'nin doğru olduğunu ve hizmetin kullanılabilir olup olmadığını doğrulamak için URL'de deneyebilirsiniz. Bir veritabanı bağlantı dizesi için veri bağlantısı Araçları'nda kullanabileceğiniz **Sunucu Gezgini** bağlantı dizesinin geçerli olduğundan ve veritabanının kullanılabilir durumda olup olmadığını doğrulayın. Bağlantınızı geri yükledikten sonra ardından temizlemek veya gerekir böylece ağa tür sağlayıcısını yeniden projeyi yeniden derleyin.|
|**Geçersiz kimlik bilgileri**. Veri kaynağı veya web hizmeti için geçerli izinleriniz olmalıdır.|Bir SQL bağlantısı için kullanıcı adı ve bağlantı dizesini veya yapılandırma dosyasında belirtilen parola veritabanı için geçerli olmalıdır. Windows kimlik doğrulaması kullanıyorsanız, veritabanına erişimi olmalıdır. Veritabanı Yöneticisi için ihtiyacı olan izinlerin her veritabanı ve bir veritabanı içinde her öğesine erişim tanımlayabilirsiniz.<br /><br />Bir web hizmetini veya bir veri hizmeti için uygun kimlik bilgilerine sahip olması gerekir. Çoğu tür sağlayıcıları, uygun kullanıcı adı ve erişim anahtarı ile ayarlanmış bir kimlik özelliği içeren bir DataContext nesnesi sağlayın.|
|**Geçersiz yol**. Bir dosya yolu geçerli değildi.|Yolun doğru olduğundan ve dosyanın var olup olmadığını doğrulayın. Ayrıca, tüm backlashes yolunda uygun şekilde teklifi veya verbatim dizesi veya Üçlü tırnak içinde dize kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Sağlayıcıları](index.md)
