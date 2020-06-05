---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6a1c8fce17e3e5a54366c2ff4dff4e6aa668f56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408666"
---
# <a name="-errorreport"></a>-errorreport

Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Açıklamalar

Bu seçenek, Visual Basic iç derleyici hatası (ıCE) için Microsoft 'un Visual Basic ekibine rapor etmenin kolay bir yolunu sağlar. Varsayılan olarak, derleyici Microsoft 'a hiçbir bilgi gönderir. Bununla birlikte, iç derleyici hatasıyla karşılaşırsanız, bu seçenek hatayı Microsoft 'a bildirebilmeniz için bu seçeneği sağlar. Bu bilgiler, Microsoft mühendisleri 'nin nedeni belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir.

Kullanıcının raporları gönderebilme özelliği makine ve Kullanıcı ilkesi izinlerine bağlıdır.

Aşağıdaki tablo, seçeneğinin etkisini özetler `-errorreport` .

|Seçenek|Davranış|
|---|---|
|`prompt`|İç derleyici hatası oluşursa, derleyicinin topladığı tam verileri görüntüleyebilmeniz için bir iletişim kutusu açılır. Hata raporunda herhangi bir hassas bilgi olup olmadığını belirleyebilir ve bunu Microsoft 'a göndermek için bir karar verebilirsiniz. Bu dosyayı göndermek isterseniz ve makine ve Kullanıcı ilkesi ayarları buna izin verirse, derleyici verileri Microsoft 'a gönderir.|
|`queue`|Hata raporunu sıralar. Yönetici ayrıcalıklarıyla oturum açtığınızda, son oturum açışınızda oluşan tüm sorunları bildirebilirsiniz (Bu işlem, her üç günde bir çok kez rapor göndermeniz istenmez). Bu, `-errorreport` seçenek belirtilmediğinde varsayılan davranıştır.|
|`send`|Bir iç derleyici hatası oluşursa ve makine ve Kullanıcı ilkesi ayarları buna izin verirseniz, derleyici verileri Microsoft 'a gönderir.<br /><br /> Raporlama, `-errorreport:send` [Windows hata bildirimi](/windows/desktop/wer/windows-error-reporting) sistem ayarları tarafından etkinleştirilmişse, Microsoft 'a otomatik olarak hata bilgilerini gönderme girişiminde bulunur. |
|`none`|Bir iç derleyici hatası oluşursa, bu durum toplanmaz veya Microsoft 'a gönderilmez.|

Derleyici, genellikle bazı kaynak kodu içeren bir hata sırasında yığını içeren verileri gönderir. `-errorreport` [-Bugreport](bugreport.md) seçeneğiyle birlikte kullanılırsa, kaynak dosyanın tamamı gönderilir.

Bu seçenek, Microsoft mühendislerinin hatayı daha kolay bir şekilde yeniden üretmesi nedeniyle, [-bugreport](bugreport.md) seçeneğiyle en iyi şekilde kullanılır.

> [!NOTE]
> `-errorreport`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod derlemeye çalışır `T2.vb` ve derleyici bir iç derleyici hatasıyla karşılaşırsa, hata raporunu Microsoft 'a göndermenizi ister.

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [-bugreport](bugreport.md)
