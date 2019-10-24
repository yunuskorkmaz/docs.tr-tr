---
title: DataViews
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 1b202af052c05ed9dc671fa20c9c366f280ec5c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774160"
---
# <a name="dataviews"></a>DataViews
@No__t_0, genellikle veri bağlama uygulamalarında kullanılan bir özellik olan bir <xref:System.Data.DataTable> depolanan verilerin farklı görünümlerini oluşturmanızı sağlar. Bir **DataView**kullanarak verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz.

 Bir **DataView** , temel alınan **DataTable**'daki verilerin dinamik bir görünümünü sağlar: içerik, sıralama ve üyelik, gerçekleşen değişiklikleri yansıtır. Bu davranış, belirli bir filtre ve/veya sıralama düzenini temel alan bir tablodan <xref:System.Data.DataRow> dizisi döndüren **DataTable**'ın **Select** yönteminden farklıdır: Bu içerik temel tablodaki değişiklikleri yansıtır, ancak üyeliği ve sıralaması statik kalır. **DataView** 'ın dinamik özellikleri, veri bağlama uygulamaları için ideal hale getirir.

 Bir **DataView** size, farklı sıralama ve filtreleme ölçütleri uygulayabileceğiniz bir veritabanı görünümü gibi tek bir veri kümesinin dinamik görünümünü sağlar. Ancak, bir veritabanı görünümünün aksine, bir **DataView** tablo olarak kabul edilemez ve birleştirilmiş tabloların bir görünümünü sağlayamaz. Kaynak tabloda bulunan sütunları dışlayamazsınız veya kaynak tabloda mevcut olmayan sütunları hesaplama sütunları gibi ekleyebilirsiniz.

 Bir **veri kümesindeki**tüm tabloların görünüm ayarlarını yönetmek için bir <xref:System.Data.DataView.DataViewManager%2A> kullanabilirsiniz. **DataViewManager** , her tablo için varsayılan görünüm ayarlarını yönetmenin kolay bir yolunu sağlar. Bir denetimi bir **veri kümesinin**birden fazla tablosuna bağlarken **DataViewManager** 'a bağlama ideal seçenektir.

## <a name="in-this-section"></a>Bu Bölümde
 [DataView oluşturma](creating-a-dataview.md) **DataTable**Için bir **DataView** oluşturmayı açıklar.

 [Verileri sıralama ve filtreleme](sorting-and-filtering-data.md) Bir **DataView** özelliklerinin belirli filtre ölçütlerine uyan veri satırlarının alt kümelerini döndürme veya belirli bir sıralama düzeninde verileri döndürme için nasıl ayarlanacağını açıklar.

 [DataRow ve DataRowViews](datarows-and-datarowviews.md) **DataView**tarafından sunulan verilere nasıl erişebileceğinizi açıklar.

 [Satırları bulma](finding-rows.md) **DataView**içinde belirli bir satırın nasıl bulunacağını açıklar.

 [Childviews ve ilişkiler](childviews-and-relations.md) Bir **DataView**kullanarak üst-alt ilişkiden veri görünümlerinin nasıl oluşturulduğunu açıklar.

 [DataView değiştirme](modifying-dataviews.md) Güncelleştirmeleri etkinleştirme veya devre dışı bırakma dahil olmak üzere **DataView**aracılığıyla temel alınan **DataTable** 'daki verilerin nasıl değiştirileceğini açıklar.

 [DataView olaylarını işleme](handling-dataview-events.md) Bir **DataView** içeriği veya sırası güncelleştirilirken bildirim almak Için **ListChanged** olayının nasıl kullanılacağını açıklar.

 [DataView yönetimi](managing-dataviews.md) Bir **veri kümesindeki**her tablo için **DataView** ayarlarını yönetmek üzere **DataViewManager** 'ın nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [ASP.NET Web uygulamaları](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100)) ASP.NET uygulamaları, Web Forms ve Web hizmetleri oluşturmak için genel bakış ve ayrıntılı, adım adım yordamlar sağlar.

 [Windows uygulamaları](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100)) Windows Forms ve konsol uygulamalarıyla çalışma hakkında ayrıntılı bilgi sağlar.

 [Veri kümeleri, DataTable ve DataView](index.md) **Veri kümesi** nesnesini ve uygulama verilerini yönetmek için nasıl kullanabileceğinizi açıklar.

 [DataTable](datatables.md) **DataTable** nesnesini ve uygulama verilerini kendi başına veya bir **veri kümesinin**parçası olarak yönetmek için nasıl kullanabileceğinizi açıklar.

 [ADO.net](../index.md) ADO.NET mimarisini ve bileşenlerini ve var olan veri kaynaklarına erişmek ve uygulama verilerini yönetmek için ADO.NET 'in nasıl kullanılacağını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
