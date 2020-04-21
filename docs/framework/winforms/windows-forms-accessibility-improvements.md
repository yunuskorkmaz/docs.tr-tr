---
title: Windows Formlar Erişilebilirlik Geliştirmeleri
description: .NET Core Windows Forms'un .NET Framework Windows Formlar ile karşılaştırıldığında erişilebilirliği nasıl geliştirmeye çalıştığı hakkında bilgi edinin.
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739754"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a>.NET Core 3.0 için Windows Forms denetimlerinde erişilebilirlik geliştirmeleri

Windows Forms, Windows Forms müşterilerini daha iyi desteklemek için erişilebilirlik teknolojileri ile nasıl çalıştığını geliştirmeye devam ediyor. Bu geliştirmeler aşağıdaki değişiklikleri içerir:

- Ekran Okuyucusu da dahil olmak üzere erişilebilirlik istemci uygulamaları yla çeşitli etkileşim alanlarındaki değişiklikler.
- Erişilebilir hiyerarşisindeki değişiklikler (UI Otomasyonu ağacında gezinmeyi geliştirme).
- Klavye gezintisindeki değişiklikler.

> [!IMPORTANT]
> .NET Framework 4.7.1 ile .NET Framework 4.8'de yapılan erişilebilirlik değişiklikleri .NET Core 3.0 ve üzeri ne kadar dır ve varsayılan olarak etkinleştirilir. .NET Framework, uygulamaların yeni erişilebilirlik davranışını devre dışı bırakmasına izin veren uyumluluk anahtarlarını destekledi. Diğer taraftan, .NET Core bu ayarları desteklemez ve uygulamaların erişilebilirlik davranışını devre dışı bırakmalarına izin vermez.
  
.NET Core 3.0 ile başlayan Windows Forms uygulamaları, ek yapılandırma olmaksızın tüm yeni erişilebilirlik özelliklerinden (.NET Framework 4.7.1 - 4.8'de tanıtılan) yararlanır.

## <a name="listbox-accessibility-support"></a>ListBox Erişilebilirlik desteği

Aşağıdaki değişiklikler <xref:System.Windows.Forms.ListBox> denetim için geçerlidir:

- Denetim için `ListBox` Etkin UI Otomasyon desteği.
- <xref:System.Windows.Automation.ScrollItemPattern> Öğelere `ListBox` ekleyerek ve öğeler arasında erişilebilirlik olay yükseltme ve işleme ve Anlatıcı navigasyon artırarak geliştirilmiş `ListBox` erişilebilirlik desteği (kapaklar kilit navigasyon doğru değildir ve istemeden denetim dışında navigasyon atmaz).

## <a name="checkedlistbox-accessibility-support"></a>CheckedListBox Erişilebilirlik desteği

Aşağıdaki değişiklikler <xref:System.Windows.Forms.CheckedListBox> denetim için geçerlidir:

- Girişler `CheckedListBox` için erişilebilirlik özellikleri tarafından sağlanan Düzeltilmiş Sınırlar.
- Genel `ListBox` ve `CheckedListBox` erişilebilirlik geliştirilmiş: düzeltilmiş özellik değerleri ve olay modeli.

## <a name="combobox-accessibility-support"></a>ComboBox Erişilebilirlik desteği

Aşağıdaki değişiklikler <xref:System.Windows.Forms.ComboBox> denetim için geçerlidir:

- Öğelerden karma `ComboBox` kodlar almak yerine öğeler için kimlik oluşturmayı etkinleştirmek için öğelerin erişilebilirlik nesnelerini alma işlemini güncelleştirin ve bu işlem, işlevin geçersiz kılınması durumunda güvenli olmayabilir. <xref:System.Object.GetHashCode%2A>

## <a name="datagridview-accessibility-support"></a>DataGridView Erişilebilirlik desteği

Aşağıdaki değişiklikler <xref:System.Windows.Forms.DataGridView> denetim için geçerlidir:

- Sütunlar, satırlar, hücreler ve ilgili üstbilgi için erişilebilirlik özellikleri tarafından sağlanan düzeltildi, `DataGridView.Bounds` sınırlayıcı dikdörtgen hesaplama geliştirilmiş performans. Tüm erişilebilirlik sınırları, tüm denetimin sınırları ve görünümü dikkate alınarak doğru bir şekilde temsil edilir.
- Erişilebilir `Value.IsReadOnly` istemci uygulamaları için sağlayan düzeltilmiş özellik değeri. Özellik artık hücreler `IsReadOnly` için doğru durumu gösterir.
- İlk hücre <xref:System.Windows.Forms.DataGridView.CellParsing> değişikliği için olay yükseltme sorunu giderildi. Hücre değeri, ilk `DataGridView` denetim etkileşimi de dahil olmak üzere herhangi bir sorun olmadan değiştirilebilir.
- Windows `DataGridView` Yüksek Karşıtlık temaları kullanırken geliştirilmiş arka plan renk kontrastı. HC#1, HC#2 ve HC Black temaları kullanırken varsayılan arka renk değiştirildi. `DataGridView`

## <a name="propertygrid-accessibility-support"></a>PropertyGrid Erişilebilirlik desteği

Aşağıdaki değişiklikler <xref:System.Windows.Forms.PropertyGrid> denetim için geçerlidir:

- Izgara girişleri için erişilebilirlik özellikleri tarafından sağlanan düzeltildi, `PropertyGrid.Bounds` sınırlayıcı dikdörtgen hesaplama geliştirilmiş performans. Şimdilik tüm erişilebilirlik sınırları, tüm denetimin sınırları ve görünümü dikkate alınarak doğru bir şekilde temsil edilir.
- Denetim türü adlarını içermemek ve denetim türü adları için çift duyuruyu önlemek için alt denetimlerin düzeltilmiş erişilebilir adları ve açıklamaları.

## <a name="toolstrip-accessibility-support"></a>ToolStrip Erişilebilirlik desteği

Aşağıdaki değişiklikler <xref:System.Windows.Forms.ToolStrip> denetim için geçerlidir:

- Gelişmiş navigasyon `ToolStrip` `MenuStrip`, `StatusStrip` , ve öğeleri. Düzeltilmiş `ToolStrip` `MenuStrip` ve shift-tab gezinme, shift-tab up-ok basıldığında menü öğeleri geri döngü, hangi alt menü öğesi öğesine gider.
- Geliştirilmiş `MenuStrip` erişilebilir gezinme, 'MenuItem' yerine 'Menü' türü alt menüler yapmak için alt menüler için düzeltilmiş menü erişilebilir kontrol türleri.

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a>PrintPreviewControl ve PrintPreviewDialog Erişilebilirlik desteği

Aşağıdaki değişiklikler yazdırma denetimleri için geçerlidir:

- Menü öğeleri arasında geliştirilmiş erişilebilir gezinme (Ekran okuyucu navigasyonu dahil) .
- Geliştirilmiş Yüksek Kontrastlı temalar desteği ve denetim öğesi daha kontrastlı yaptı.

## <a name="stringcollectioneditor-accessibility-support"></a>StringCollectionEditor Erişilebilirlik desteği

Windows Forms tasarımcısı artık geliştirilmiş erişilebilirlik desteğiyle dize koleksiyonu düzenleyicisini kullanır.

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a>MonthCalendar Erişilebilirlik desteği (.NET Core 3.1'de mevcuttur)

Aşağıdaki değişiklikler <xref:System.Windows.Forms.MonthCalendar> denetim için geçerlidir:

- Kontrol etmek için `MonthCalendar` UI Automation sunucu sağlayıcıları eklendi, UI Automation Grid deseni ve Tablo desen sağlayıcıları eklendi.
- Değiştirilen _tablo_ erişilebilir denetim türü için `MonthCalendar` _takvim_ erişilebilir kontrol türü için durum dışında `MonthCalendar` denetim denetim erişilebilir adı tanımlayan bir önceki etiket denetimi varsa, bu özel durumda erişilebilir kontrol türü _tablo_olur .
- Denetim için `MonthCalendar` seçilen tarihin geliştirilmiş duyurusu.
- Ekran `MonthCalendar` okuyucular ve diğer erişilebilirlik araçları için geliştirilmiş kontrol desteği. Şu anda, kullanıcılar denetim öğelerinde gezinebilir ve yalnızca klavye girişi kullanarak bu öğelerle etkileşimkurabilir. Ekran Okuyucusu ile, kontrol öğeleri arasında gezinmek için CAPS + ok tuşlarını kullanın ve varsayılan eylemi çağırmak için CAPS + Girin.
- Odaklanan bir dikdörtgen `MonthCalendar` ile alt öğeler arasında geliştirilmiş ok tuşu gezinme: Ekran Okuyucusu için mavi odak dikdörtgeni.
- Sağlanan koordinatlar tarafından alt `MonthCalendar` erişilebilir öğe elde `MonthCalendar` etmek için izin vermek için denetim öğeleri için isabet test eylemi için geliştirilmiş erişilebilirlik.

## <a name="tooltips-accessibility-available-in-net-core-31"></a>ToolTips erişilebilirlik (.NET Core 3.1'de mevcuttur)

- NVDA ve Ekran Okuyucu gibi ekran okuyucu uygulamaları tarafından bir araç ipucu metni duyurmak için yeteneği eklendi. Ekran okuyucu uygulaması artık araç ipuçlarını göstermek üzere yapılandırılan herhangi bir Windows Forms denetiminin klavye veya fare araç ucunun metnini duyurabilir.

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a>DataGridView, PropertyGrid, ListBox, ComboBox, ToolStrip ve diğer denetimler için UI otomasyon desteği

UI Automation desteği çalışma zamanında denetimler için etkinleştirilir, ancak tasarım süresi boyunca kullanılmaz. UI otomasyonuna genel bir bakış için [UI Automation Genel Bakış](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Erişilebilirlik En İyi Uygulamalar](../ui-automation/accessibility-best-practices.md).
