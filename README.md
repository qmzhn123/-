1、数据集处理
首先删除已损坏的图片（检查.ipynb），再删除多余的xml标注文件（检查.ipynb），然后把部分图片大小与标注不符的进行修改（修改大小.ipynb），最后把xml文件转换成json文件（json.ipynb）。训练集1916张，验证集233张。
2、模型训练优化
训练模型:python tools/train.py -c configs/picodet/legacy_model/application/layout_analysis/picodet_lcnet_x1_0_layout.yml --eval
转换inference模型：python tools/export_model.py -c configs/picodet/legacy_model/application/layout_analysis/picodet_lcnet_x1_0_layout.yml -o weights=output/picodet_lcnet_x1_0_layout/best_model --output_dir=D:/PaddleDetection/output_inference
转换onnx模型：paddle2onnx --model_dir D:/PaddleDetection/output_inference/picodet_lcnet_x1_0_layout/60-50 --model_filename model.pdmodel --params_filename model.pdiparams --save_file output_inference/model.onnx --enable_onnx_checker True
