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
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="7d293-102">Nasıl yapılır: Görüntü Meta Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="7d293-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="7d293-103">Bazı resim dosyaları, görüntünün özelliklerini belirlemek için okuyabileceğiniz meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="7d293-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="7d293-104">Örneğin, dijital fotoğraf, görüntüyü yakalamak için kullanılan kameranın molası ve modelini belirlemek için okuyabileceğiniz meta veriler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7d293-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="7d293-105">GDI+ ile varolan meta verileri okuyabilir ve görüntü dosyalarına yeni meta veriler de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d293-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="7d293-106">GDI+, tek bir meta veri <xref:System.Drawing.Imaging.PropertyItem> parçasını bir nesnede depolar.</span><span class="sxs-lookup"><span data-stu-id="7d293-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="7d293-107">Bir dosyadan <xref:System.Drawing.Image.PropertyItems%2A> tüm <xref:System.Drawing.Image> meta verileri almak için bir nesnenin özelliğini okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d293-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="7d293-108">Özellik <xref:System.Drawing.Image.PropertyItems%2A> bir dizi <xref:System.Drawing.Imaging.PropertyItem> nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d293-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="7d293-109">Bir <xref:System.Drawing.Imaging.PropertyItem> nesnenin aşağıdaki dört `Id` `Value`özelliği `Len`vardır: , , ve `Type`.</span><span class="sxs-lookup"><span data-stu-id="7d293-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="7d293-110">Kimlik</span><span class="sxs-lookup"><span data-stu-id="7d293-110">Id</span></span>

<span data-ttu-id="7d293-111">Meta veri öğesini tanımlayan bir etiket.</span><span class="sxs-lookup"><span data-stu-id="7d293-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="7d293-112">Atanabilecek <xref:System.Drawing.Imaging.PropertyItem.Id%2A> bazı değerler aşağıdaki tabloda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="7d293-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="7d293-113">Hexadecimal değer</span><span class="sxs-lookup"><span data-stu-id="7d293-113">Hexadecimal value</span></span>|<span data-ttu-id="7d293-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d293-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="7d293-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="7d293-115">0x0320</span></span><br /><br /> <span data-ttu-id="7d293-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="7d293-116">0x010F</span></span><br /><br /> <span data-ttu-id="7d293-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="7d293-117">0x0110</span></span><br /><br /> <span data-ttu-id="7d293-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="7d293-118">0x9003</span></span><br /><br /> <span data-ttu-id="7d293-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="7d293-119">0x829A</span></span><br /><br /> <span data-ttu-id="7d293-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="7d293-120">0x5090</span></span><br /><br /> <span data-ttu-id="7d293-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="7d293-121">0x5091</span></span>|<span data-ttu-id="7d293-122">Resim başlığı</span><span class="sxs-lookup"><span data-stu-id="7d293-122">Image title</span></span><br /><br /> <span data-ttu-id="7d293-123">Ekipman üreticisi</span><span class="sxs-lookup"><span data-stu-id="7d293-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="7d293-124">Ekipman modeli</span><span class="sxs-lookup"><span data-stu-id="7d293-124">Equipment model</span></span><br /><br /> <span data-ttu-id="7d293-125">ExifDTOrijinal</span><span class="sxs-lookup"><span data-stu-id="7d293-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="7d293-126">Exif pozlama süresi</span><span class="sxs-lookup"><span data-stu-id="7d293-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="7d293-127">Parlaklık tablosu</span><span class="sxs-lookup"><span data-stu-id="7d293-127">Luminance table</span></span><br /><br /> <span data-ttu-id="7d293-128">Chrominance tablosu</span><span class="sxs-lookup"><span data-stu-id="7d293-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="7d293-129">Değer</span><span class="sxs-lookup"><span data-stu-id="7d293-129">Value</span></span>

<span data-ttu-id="7d293-130">Bir dizi değer.</span><span class="sxs-lookup"><span data-stu-id="7d293-130">An array of values.</span></span> <span data-ttu-id="7d293-131">Değerlerin biçimi <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7d293-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="7d293-132">Len</span><span class="sxs-lookup"><span data-stu-id="7d293-132">Len</span></span>

<span data-ttu-id="7d293-133"><xref:System.Drawing.Imaging.PropertyItem.Value%2A> Özellik tarafından işaret edilen değerler dizisinin uzunluğu (baytlarda).</span><span class="sxs-lookup"><span data-stu-id="7d293-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="7d293-134">Tür</span><span class="sxs-lookup"><span data-stu-id="7d293-134">Type</span></span>

<span data-ttu-id="7d293-135">Dizideki değerlerin veri türü `Value` özelliğitarafından işaret edilir.</span><span class="sxs-lookup"><span data-stu-id="7d293-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="7d293-136">`Type` Özellik değerleri ile gösterilen biçimler aşağıdaki tabloda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="7d293-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="7d293-137">Sayısal değer</span><span class="sxs-lookup"><span data-stu-id="7d293-137">Numeric value</span></span>|<span data-ttu-id="7d293-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d293-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="7d293-139">1</span><span class="sxs-lookup"><span data-stu-id="7d293-139">1</span></span>|<span data-ttu-id="7d293-140">Bir `Byte`</span><span class="sxs-lookup"><span data-stu-id="7d293-140">A `Byte`</span></span>|
|<span data-ttu-id="7d293-141">2</span><span class="sxs-lookup"><span data-stu-id="7d293-141">2</span></span>|<span data-ttu-id="7d293-142">ASCII `Byte` olarak kodlanmış bir dizi nesne</span><span class="sxs-lookup"><span data-stu-id="7d293-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="7d293-143">3</span><span class="sxs-lookup"><span data-stu-id="7d293-143">3</span></span>|<span data-ttu-id="7d293-144">16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="7d293-144">A 16-bit integer</span></span>|
|<span data-ttu-id="7d293-145">4</span><span class="sxs-lookup"><span data-stu-id="7d293-145">4</span></span>|<span data-ttu-id="7d293-146">32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="7d293-146">A 32-bit integer</span></span>|
|<span data-ttu-id="7d293-147">5</span><span class="sxs-lookup"><span data-stu-id="7d293-147">5</span></span>|<span data-ttu-id="7d293-148">Rasyonel bir `Byte` sayıyı temsil eden iki nesneden oluşan bir dizi</span><span class="sxs-lookup"><span data-stu-id="7d293-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="7d293-149">6</span><span class="sxs-lookup"><span data-stu-id="7d293-149">6</span></span>|<span data-ttu-id="7d293-150">Kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="7d293-150">Not used</span></span>|
|<span data-ttu-id="7d293-151">7</span><span class="sxs-lookup"><span data-stu-id="7d293-151">7</span></span>|<span data-ttu-id="7d293-152">Tanımsız</span><span class="sxs-lookup"><span data-stu-id="7d293-152">Undefined</span></span>|
|<span data-ttu-id="7d293-153">8</span><span class="sxs-lookup"><span data-stu-id="7d293-153">8</span></span>|<span data-ttu-id="7d293-154">Kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="7d293-154">Not used</span></span>|
|<span data-ttu-id="7d293-155">9</span><span class="sxs-lookup"><span data-stu-id="7d293-155">9</span></span>|`SLong`|
|<span data-ttu-id="7d293-156">10</span><span class="sxs-lookup"><span data-stu-id="7d293-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="7d293-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d293-157">Example</span></span>
  
<span data-ttu-id="7d293-158">Aşağıdaki kod örneği, dosyadaki `FakePhoto.jpg`yedi meta veri parçasını okur ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7d293-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="7d293-159">Listedeki ikinci (dizin 1) <xref:System.Drawing.Imaging.PropertyItem.Id%2A> özellik öğesi 0x010F <xref:System.Drawing.Imaging.PropertyItem.Type%2A> (ekipman üreticisi) ve 2 (ASCII kodlanmış bayt dizisi) vardır.</span><span class="sxs-lookup"><span data-stu-id="7d293-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="7d293-160">Kod örneği, o özellik öğesinin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7d293-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="7d293-161">Kod aşağıdakine benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="7d293-161">The code produces output similar to the following:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="7d293-162">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7d293-162">Compiling the Code</span></span>

<span data-ttu-id="7d293-163">Önceki örnek, Windows Formları ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan , gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d293-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="7d293-164">Formun <xref:System.Windows.Forms.Control.Paint> olayını işleyebilir ve bu kodu boya olayı işleyicisine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d293-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="7d293-165">Sisteminizde `FakePhoto.jpg` geçerli bir görüntü adı ve yol ile `System.Drawing.Imaging` değiştirmeniz ve ad alanını almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d293-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d293-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d293-166">See also</span></span>

- [<span data-ttu-id="7d293-167">Resimler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="7d293-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="7d293-168">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="7d293-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
