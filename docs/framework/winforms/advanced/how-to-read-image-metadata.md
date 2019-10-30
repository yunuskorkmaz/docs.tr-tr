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
ms.openlocfilehash: cd3b636f8f0058d4a8eacc656f95d5f46b8967e2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040749"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="9950b-102">Nasıl yapılır: Görüntü Meta Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="9950b-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="9950b-103">Bazı görüntü dosyaları, görüntünün özelliklerini belirleyebilmek için okuyabilmeniz gereken meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="9950b-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="9950b-104">Örneğin, dijital bir fotoğrafta görüntüyü yakalamak için kullanılan kameranın marka ve modelini öğrenmek için okuyabilmeniz gereken meta veriler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9950b-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="9950b-105">GDI+ ile, mevcut meta verileri okuyabilir ve resim dosyalarına yeni meta veriler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9950b-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="9950b-106">GDI+ bir <xref:System.Drawing.Imaging.PropertyItem> nesnesinde tek bir meta veri parçası depolar.</span><span class="sxs-lookup"><span data-stu-id="9950b-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="9950b-107">Bir dosyanın tüm meta verilerini almak için bir <xref:System.Drawing.Image> nesnesinin <xref:System.Drawing.Image.PropertyItems%2A> özelliğini okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9950b-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="9950b-108"><xref:System.Drawing.Image.PropertyItems%2A> özelliği <xref:System.Drawing.Imaging.PropertyItem> nesnelerinin bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9950b-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="9950b-109"><xref:System.Drawing.Imaging.PropertyItem> nesne aşağıdaki dört özelliğe sahiptir: `Id`, `Value`, `Len`ve `Type`.</span><span class="sxs-lookup"><span data-stu-id="9950b-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="9950b-110">Numarasını</span><span class="sxs-lookup"><span data-stu-id="9950b-110">Id</span></span>

<span data-ttu-id="9950b-111">Meta veri öğesini tanımlayan bir etiket.</span><span class="sxs-lookup"><span data-stu-id="9950b-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="9950b-112"><xref:System.Drawing.Imaging.PropertyItem.Id%2A> atanabileceği bazı değerler aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9950b-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="9950b-113">Onaltılık değer</span><span class="sxs-lookup"><span data-stu-id="9950b-113">Hexadecimal value</span></span>|<span data-ttu-id="9950b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9950b-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="9950b-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="9950b-115">0x0320</span></span><br /><br /> <span data-ttu-id="9950b-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="9950b-116">0x010F</span></span><br /><br /> <span data-ttu-id="9950b-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="9950b-117">0x0110</span></span><br /><br /> <span data-ttu-id="9950b-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="9950b-118">0x9003</span></span><br /><br /> <span data-ttu-id="9950b-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="9950b-119">0x829A</span></span><br /><br /> <span data-ttu-id="9950b-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="9950b-120">0x5090</span></span><br /><br /> <span data-ttu-id="9950b-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="9950b-121">0x5091</span></span>|<span data-ttu-id="9950b-122">Görüntü başlığı</span><span class="sxs-lookup"><span data-stu-id="9950b-122">Image title</span></span><br /><br /> <span data-ttu-id="9950b-123">Ekipman üreticisi</span><span class="sxs-lookup"><span data-stu-id="9950b-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="9950b-124">Ekipman modeli</span><span class="sxs-lookup"><span data-stu-id="9950b-124">Equipment model</span></span><br /><br /> <span data-ttu-id="9950b-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="9950b-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="9950b-126">Exif etkilenme süresi</span><span class="sxs-lookup"><span data-stu-id="9950b-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="9950b-127">Işıklılık tablosu</span><span class="sxs-lookup"><span data-stu-id="9950b-127">Luminance table</span></span><br /><br /> <span data-ttu-id="9950b-128">Kınance tablosu</span><span class="sxs-lookup"><span data-stu-id="9950b-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="9950b-129">Değer</span><span class="sxs-lookup"><span data-stu-id="9950b-129">Value</span></span>

<span data-ttu-id="9950b-130">Bir değerler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9950b-130">An array of values.</span></span> <span data-ttu-id="9950b-131">Değerlerin biçimi <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9950b-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="9950b-132">Tepe</span><span class="sxs-lookup"><span data-stu-id="9950b-132">Len</span></span>

<span data-ttu-id="9950b-133"><xref:System.Drawing.Imaging.PropertyItem.Value%2A> özelliği tarafından işaret edilen değerlerin dizisinin uzunluğu (bayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="9950b-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="9950b-134">Tür</span><span class="sxs-lookup"><span data-stu-id="9950b-134">Type</span></span>

<span data-ttu-id="9950b-135">`Value` özelliği tarafından işaret edilen dizideki değerlerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="9950b-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="9950b-136">`Type` özellik değerleri tarafından belirtilen biçimler aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9950b-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="9950b-137">Sayısal değer</span><span class="sxs-lookup"><span data-stu-id="9950b-137">Numeric value</span></span>|<span data-ttu-id="9950b-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9950b-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="9950b-139">1\.</span><span class="sxs-lookup"><span data-stu-id="9950b-139">1</span></span>|<span data-ttu-id="9950b-140">Bir `Byte`</span><span class="sxs-lookup"><span data-stu-id="9950b-140">A `Byte`</span></span>|
|<span data-ttu-id="9950b-141">2</span><span class="sxs-lookup"><span data-stu-id="9950b-141">2</span></span>|<span data-ttu-id="9950b-142">ASCII olarak kodlanan `Byte` nesneleri dizisi</span><span class="sxs-lookup"><span data-stu-id="9950b-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="9950b-143">3</span><span class="sxs-lookup"><span data-stu-id="9950b-143">3</span></span>|<span data-ttu-id="9950b-144">16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="9950b-144">A 16-bit integer</span></span>|
|<span data-ttu-id="9950b-145">4</span><span class="sxs-lookup"><span data-stu-id="9950b-145">4</span></span>|<span data-ttu-id="9950b-146">32 bitlik bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="9950b-146">A 32-bit integer</span></span>|
|<span data-ttu-id="9950b-147">5</span><span class="sxs-lookup"><span data-stu-id="9950b-147">5</span></span>|<span data-ttu-id="9950b-148">Bir Rational Number öğesini temsil eden iki `Byte` nesne dizisi</span><span class="sxs-lookup"><span data-stu-id="9950b-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="9950b-149">6</span><span class="sxs-lookup"><span data-stu-id="9950b-149">6</span></span>|<span data-ttu-id="9950b-150">Kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="9950b-150">Not used</span></span>|
|<span data-ttu-id="9950b-151">7</span><span class="sxs-lookup"><span data-stu-id="9950b-151">7</span></span>|<span data-ttu-id="9950b-152">Tanımlayan</span><span class="sxs-lookup"><span data-stu-id="9950b-152">Undefined</span></span>|
|<span data-ttu-id="9950b-153">8</span><span class="sxs-lookup"><span data-stu-id="9950b-153">8</span></span>|<span data-ttu-id="9950b-154">Kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="9950b-154">Not used</span></span>|
|<span data-ttu-id="9950b-155">9</span><span class="sxs-lookup"><span data-stu-id="9950b-155">9</span></span>|`SLong`|
|<span data-ttu-id="9950b-156">10</span><span class="sxs-lookup"><span data-stu-id="9950b-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="9950b-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="9950b-157">Example</span></span>
  
<span data-ttu-id="9950b-158">Aşağıdaki kod örneği, `FakePhoto.jpg`dosyadaki yedi meta veri parçasını okur ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9950b-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="9950b-159">Listedeki ikinci (Dizin 1) özellik öğesi <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (ekipman üreticisi) ve <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII kodlu bayt dizisi).</span><span class="sxs-lookup"><span data-stu-id="9950b-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="9950b-160">Kod örneği, bu özellik öğesinin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9950b-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="9950b-161">Kod aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="9950b-161">The code produces output similar to the following:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="9950b-162">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9950b-162">Compiling the Code</span></span>

<span data-ttu-id="9950b-163">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan <xref:System.Windows.Forms.PaintEventArgs> `e`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9950b-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="9950b-164">Formun <xref:System.Windows.Forms.Control.Paint> olayını işleyin ve bu kodu Paint olay işleyicisine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9950b-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="9950b-165">`FakePhoto.jpg`, sisteminizde geçerli bir görüntü adı ve yolu ile değiştirmeniz ve `System.Drawing.Imaging` ad alanını içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9950b-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="9950b-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9950b-166">See also</span></span>

- [<span data-ttu-id="9950b-167">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="9950b-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="9950b-168">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="9950b-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
