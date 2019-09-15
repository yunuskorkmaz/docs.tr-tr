---
title: 'Nasıl yapılır: Görüntü Meta Verilerini Okuma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 8294bc6596c408160a50d9d7d5e6154f66025c73
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988566"
---
# <a name="how-to-read-image-metadata"></a>Nasıl yapılır: Görüntü Meta Verilerini Okuma
Bazı görüntü dosyaları, görüntünün özelliklerini belirleyebilmek için okuyabilmeniz gereken meta veriler içerir. Örneğin, dijital bir fotoğrafta görüntüyü yakalamak için kullanılan kameranın marka ve modelini öğrenmek için okuyabilmeniz gereken meta veriler bulunabilir. GDI+ ile, mevcut meta verileri okuyabilir ve resim dosyalarına yeni meta veriler yazabilirsiniz.  
  
 GDI+ bir <xref:System.Drawing.Imaging.PropertyItem> nesne içinde tek bir meta veri parçası depolar. Bir dosyanın tüm meta <xref:System.Drawing.Image.PropertyItems%2A> verilerini almak için <xref:System.Drawing.Image> bir nesnenin özelliğini okuyabilirsiniz. Özelliği bir <xref:System.Drawing.Imaging.PropertyItem> nesne dizisi döndürür. <xref:System.Drawing.Image.PropertyItems%2A>  
  
 Bir <xref:System.Drawing.Imaging.PropertyItem> nesne aşağıdaki dört özelliğe sahiptir: `Id`, `Value`, `Len`, ve `Type`.  
  
## <a name="id"></a>Id  
 Meta veri öğesini tanımlayan bir etiket. İçin <xref:System.Drawing.Imaging.PropertyItem.Id%2A> atanabilecek bazı değerler aşağıdaki tabloda gösterilmiştir.  
  
|Onaltılık değer|Açıklama|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Görüntü başlığı<br /><br /> Ekipman üreticisi<br /><br /> Ekipman modeli<br /><br /> ExifDTOriginal<br /><br /> Exif etkilenme süresi<br /><br /> Işıklılık tablosu<br /><br /> Kınance tablosu|  
  
## <a name="value"></a>Değer  
 Bir değerler dizisi. Değerlerin biçimi, <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özelliği tarafından belirlenir.  
  
## <a name="len"></a>Tepe  
 <xref:System.Drawing.Imaging.PropertyItem.Value%2A> Özelliği tarafından işaret edilen değerlerin dizisinin uzunluğu (bayt cinsinden).  
  
## <a name="type"></a>Tür  
 Dizide, `Value` özelliği tarafından işaret edilen değerlerin veri türü. `Type` Özellik değerleri tarafından belirtilen biçimler aşağıdaki tabloda gösterilmiştir  
  
|Sayısal değer|Açıklama|  
|-------------------|-----------------|  
|1\.|A`Byte`|  
|2|ASCII olarak kodlanmış `Byte` bir nesne dizisi|  
|3|16 bit tam sayı|  
|4|32 bitlik bir tamsayı|  
|5|Bir Rational Number öğesini `Byte` temsil eden iki nesne dizisi|  
|6|Kullanılan değil|  
|7|Tanımlanmadı|  
|8|Kullanılan değil|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği, dosyadaki `FakePhoto.jpg`yedi meta veri parçasını okur ve görüntüler. Listedeki <xref:System.Drawing.Imaging.PropertyItem.Id%2A> ikinci (Dizin 1) özellik öğesi 0x010F (ekipman üreticisi) ve <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII kodlamalı bayt dizisi). Kod örneği, bu özellik öğesinin değerini görüntüler.  
  
 Kod aşağıdakine benzer bir çıktı üretir:  
 
```output
 Property Item 0
  
 id: 0x320
  
 type: 2
 
 length: 16 bytes 
  
 Property Item 1
  
 id: 0x10f
  
 type: 2 
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan gerektirir `e`. Formun <xref:System.Windows.Forms.Control.Paint> olayını işleyin ve bu kodu Paint olay işleyicisine yapıştırın. ' İ sisteminizde `FakePhoto.jpg` geçerli bir görüntü adı ve yolu ile değiştirmeniz ve `System.Drawing.Imaging` ad alanını içeri aktarmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
