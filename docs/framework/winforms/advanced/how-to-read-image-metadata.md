---
title: 'Nasıl yapılır: Görüntü Meta Verilerini Okuma'
desription: Learn how to read the Windows Forms PropertyItems property of an Image object to retrieve all the metadata from a file.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 814cb17feba1e1e3a42b2bc403b0b4c828caf90e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174672"
---
# <a name="how-to-read-image-metadata"></a>Nasıl yapılır: Görüntü Meta Verilerini Okuma

Bazı görüntü dosyaları, görüntünün özelliklerini belirleyebilmek için okuyabilmeniz gereken meta veriler içerir. Örneğin, dijital bir fotoğrafta görüntüyü yakalamak için kullanılan kameranın marka ve modelini öğrenmek için okuyabilmeniz gereken meta veriler bulunabilir. GDI+ ile, mevcut meta verileri okuyabilir ve resim dosyalarına yeni meta veriler yazabilirsiniz.

GDI+ bir nesne içinde tek bir meta veri parçası depolar <xref:System.Drawing.Imaging.PropertyItem> . <xref:System.Drawing.Image.PropertyItems%2A> <xref:System.Drawing.Image> Bir dosyanın tüm meta verilerini almak için bir nesnenin özelliğini okuyabilirsiniz. <xref:System.Drawing.Image.PropertyItems%2A>Özelliği bir nesne dizisi döndürür <xref:System.Drawing.Imaging.PropertyItem> .

Bir <xref:System.Drawing.Imaging.PropertyItem> nesne aşağıdaki dört özelliğe sahiptir: `Id` , `Value` , `Len` , ve `Type` .

## <a name="id"></a>Kimlik

Meta veri öğesini tanımlayan bir etiket. İçin atanabilecek bazı değerler <xref:System.Drawing.Imaging.PropertyItem.Id%2A> Aşağıdaki tabloda gösterilmiştir:

|Onaltılık değer|Açıklama|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Görüntü başlığı<br /><br /> Ekipman üreticisi<br /><br /> Ekipman modeli<br /><br /> ExifDTOriginal<br /><br /> Exif etkilenme süresi<br /><br /> Işıklılık tablosu<br /><br /> Kınance tablosu|

## <a name="value"></a>Değer

Bir değerler dizisi. Değerlerin biçimi, özelliği tarafından belirlenir <xref:System.Drawing.Imaging.PropertyItem.Type%2A> .

## <a name="len"></a>Len

Özelliği tarafından işaret edilen değerlerin dizisinin uzunluğu (bayt cinsinden) <xref:System.Drawing.Imaging.PropertyItem.Value%2A> .

## <a name="type"></a>Tür

Dizide, özelliği tarafından işaret edilen değerlerin veri türü `Value` . Özellik değerleri tarafından belirtilen biçimler `Type` Aşağıdaki tabloda gösterilmiştir:

|Sayısal değer|Açıklama|
|-------------------|-----------------|
|1|`Byte`|
|2|`Byte`ASCII olarak kodlanmış bir nesne dizisi|
|3|16 bit tam sayı|
|4|32 bitlik bir tamsayı|
|5|`Byte`Bir Rational Number öğesini temsil eden iki nesne dizisi|
|6|Kullanılmıyor|
|7|Tanımlayan|
|8|Kullanılmıyor|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Örnek
  
Aşağıdaki kod örneği, dosyadaki yedi meta veri parçasını okur ve görüntüler `FakePhoto.jpg` . Listedeki ikinci (Dizin 1) özellik öğesi <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (ekipman üreticisi) ve <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII kodlamalı bayt dizisi). Kod örneği, bu özellik öğesinin değerini görüntüler.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

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

## <a name="compiling-the-code"></a>Kod Derleniyor

Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> `e` olay işleyicisinin bir parametresi olan gerektirir <xref:System.Windows.Forms.Control.Paint> . Formun <xref:System.Windows.Forms.Control.Paint> olayını işleyin ve bu kodu Paint olay işleyicisine yapıştırın. ' `FakePhoto.jpg` İ sisteminizde geçerli bir görüntü adı ve yolu ile değiştirmeniz ve ad alanını içeri aktarmanız gerekir `System.Drawing.Imaging` .

## <a name="see-also"></a>Ayrıca bkz.

- [Resimler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
