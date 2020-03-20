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
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182517"
---
# <a name="how-to-read-image-metadata"></a>Nasıl yapılır: Görüntü Meta Verilerini Okuma

Bazı resim dosyaları, görüntünün özelliklerini belirlemek için okuyabileceğiniz meta veriler içerir. Örneğin, dijital fotoğraf, görüntüyü yakalamak için kullanılan kameranın molası ve modelini belirlemek için okuyabileceğiniz meta veriler içerebilir. GDI+ ile varolan meta verileri okuyabilir ve görüntü dosyalarına yeni meta veriler de yazabilirsiniz.

GDI+, tek bir meta veri <xref:System.Drawing.Imaging.PropertyItem> parçasını bir nesnede depolar. Bir dosyadan <xref:System.Drawing.Image.PropertyItems%2A> tüm <xref:System.Drawing.Image> meta verileri almak için bir nesnenin özelliğini okuyabilirsiniz. Özellik <xref:System.Drawing.Image.PropertyItems%2A> bir dizi <xref:System.Drawing.Imaging.PropertyItem> nesne döndürür.

Bir <xref:System.Drawing.Imaging.PropertyItem> nesnenin aşağıdaki dört `Id` `Value`özelliği `Len`vardır: , , ve `Type`.

## <a name="id"></a>Kimlik

Meta veri öğesini tanımlayan bir etiket. Atanabilecek <xref:System.Drawing.Imaging.PropertyItem.Id%2A> bazı değerler aşağıdaki tabloda gösterilir:

|Hexadecimal değer|Açıklama|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Resim başlığı<br /><br /> Ekipman üreticisi<br /><br /> Ekipman modeli<br /><br /> ExifDTOrijinal<br /><br /> Exif pozlama süresi<br /><br /> Parlaklık tablosu<br /><br /> Chrominance tablosu|

## <a name="value"></a>Değer

Bir dizi değer. Değerlerin biçimi <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özellik tarafından belirlenir.

## <a name="len"></a>Len

<xref:System.Drawing.Imaging.PropertyItem.Value%2A> Özellik tarafından işaret edilen değerler dizisinin uzunluğu (baytlarda).

## <a name="type"></a>Tür

Dizideki değerlerin veri türü `Value` özelliğitarafından işaret edilir. `Type` Özellik değerleri ile gösterilen biçimler aşağıdaki tabloda gösterilir:

|Sayısal değer|Açıklama|
|-------------------|-----------------|
|1|Bir `Byte`|
|2|ASCII `Byte` olarak kodlanmış bir dizi nesne|
|3|16 bit tamsayı|
|4|32 bit tamsayı|
|5|Rasyonel bir `Byte` sayıyı temsil eden iki nesneden oluşan bir dizi|
|6|Kullanılmıyor|
|7|Tanımsız|
|8|Kullanılmıyor|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Örnek
  
Aşağıdaki kod örneği, dosyadaki `FakePhoto.jpg`yedi meta veri parçasını okur ve görüntüler. Listedeki ikinci (dizin 1) <xref:System.Drawing.Imaging.PropertyItem.Id%2A> özellik öğesi 0x010F <xref:System.Drawing.Imaging.PropertyItem.Type%2A> (ekipman üreticisi) ve 2 (ASCII kodlanmış bayt dizisi) vardır. Kod örneği, o özellik öğesinin değerini görüntüler.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

Kod aşağıdakine benzer çıktı üretir:

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

## <a name="compiling-the-code"></a>Kod Derleniyor

Önceki örnek, Windows Formları ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan , gerektirir. Formun <xref:System.Windows.Forms.Control.Paint> olayını işleyebilir ve bu kodu boya olayı işleyicisine yapıştırın. Sisteminizde `FakePhoto.jpg` geçerli bir görüntü adı ve yol ile `System.Drawing.Imaging` değiştirmeniz ve ad alanını almanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Resimler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
