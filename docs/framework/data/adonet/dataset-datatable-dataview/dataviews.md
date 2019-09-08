---
title: DataViews
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 8a06accb11631f2dce6b0d39587d7274223c0e68
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786351"
---
# <a name="dataviews"></a>DataViews
, Genellikle veri bağlama uygulamalarında kullanılan bir özellik olan, <xref:System.Data.DataView> içinde depolanan verilerin farklı görünümlerini <xref:System.Data.DataTable>oluşturmanızı sağlar. Bir **DataView**kullanarak verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz.  
  
 Bir **DataView** , temel alınan **DataTable**'daki verilerin dinamik bir görünümünü sağlar: içerik, sıralama ve üyelik, gerçekleşen değişiklikleri yansıtır. Bu davranış, belirli bir filtre ve/veyasıralama düzenini temel alan bir <xref:System.Data.DataRow> tablodan dizi döndüren DataTable 'ın **Select** yönteminden farklıdır: Bu içerik, temel tablodaki değişiklikleri yansıtır, ancak üyeliği ve sıralama statik kalır. **DataView** 'ın dinamik özellikleri, veri bağlama uygulamaları için ideal hale getirir.  
  
 Bir **DataView** size, farklı sıralama ve filtreleme ölçütleri uygulayabileceğiniz bir veritabanı görünümü gibi tek bir veri kümesinin dinamik görünümünü sağlar. Ancak, bir veritabanı görünümünün aksine, bir **DataView** tablo olarak kabul edilemez ve birleştirilmiş tabloların bir görünümünü sağlayamaz. Kaynak tabloda mevcut olmayan sütunları da dışlayamazsınız ve kaynak tabloda bulunmayan hesaplama sütunları gibi sütunları ekleyebilirsiniz.  
  
 Bir **veri kümesindeki**tüm <xref:System.Data.DataView.DataViewManager%2A> tablolar için görünüm ayarlarını yönetmek üzere bir kullanabilirsiniz. **DataViewManager** , her tablo için varsayılan görünüm ayarlarını yönetmenin kolay bir yolunu sağlar. Bir denetimi bir **veri kümesinin**birden fazla tablosuna bağlarken **DataViewManager** 'a bağlama ideal seçenektir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataView Oluşturma](creating-a-dataview.md)  
 **DataTable**Için bir **DataView** oluşturmayı açıklar.  
  
 [Verileri Sıralama ve Filtreleme](sorting-and-filtering-data.md)  
 Bir **DataView** özelliklerinin belirli filtre ölçütlerine uyan veri satırlarının alt kümelerini döndürme veya belirli bir sıralama düzeninde verileri döndürme için nasıl ayarlanacağını açıklar.  
  
 [DataRows ve DataRowViews](datarows-and-datarowviews.md)  
 **DataView**tarafından sunulan verilere nasıl erişebileceğinizi açıklar.  
  
 [Satırları Bulma](finding-rows.md)  
 **DataView**içinde belirli bir satırın nasıl bulunacağını açıklar.  
  
 [ChildViews ve İlişkileri](childviews-and-relations.md)  
 Bir **DataView**kullanarak üst-alt ilişkiden veri görünümlerinin nasıl oluşturulduğunu açıklar.  
  
 [DataView Değiştirme](modifying-dataviews.md)  
 Güncelleştirmeleri etkinleştirme veya devre dışı bırakma dahil olmak üzere **DataView**aracılığıyla temel alınan **DataTable** 'daki verilerin nasıl değiştirileceğini açıklar.  
  
 [DataView Olaylarını İşleme](handling-dataview-events.md)  
 Bir **DataView** içeriği veya sırası güncelleştirilirken bildirim almak Için **ListChanged** olayının nasıl kullanılacağını açıklar.  
  
 [DataView Yönetme](managing-dataviews.md)  
 Bir **veri kümesindeki**her tablo için **DataView** ayarlarını yönetmek üzere **DataViewManager** 'ın nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ASP.NET Web Uygulamaları](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))  
 ASP.NET uygulamaları, Web Forms ve Web hizmetleri oluşturmak için genel bakış ve ayrıntılı, adım adım yordamlar sağlar.  
  
 [Windows uygulamaları](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))  
 Windows Forms ve konsol uygulamalarıyla çalışma hakkında ayrıntılı bilgi sağlar.  
  
 [DataSets, DataTables ve DataViews](index.md)  
 **Veri kümesi** nesnesini ve uygulama verilerini yönetmek için nasıl kullanabileceğinizi açıklar.  
  
 [DataTables](datatables.md)  
 **DataTable** nesnesini ve uygulama verilerini kendi başına veya bir **veri kümesinin**parçası olarak yönetmek için nasıl kullanabileceğinizi açıklar.  
  
 [ADO.NET](../index.md)  
 ADO.NET mimarisini ve bileşenlerini ve var olan veri kaynaklarına erişmek ve uygulama verilerini yönetmek için ADO.NET 'in nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
